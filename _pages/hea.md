---
layout: default
title: "High Entropy Alloys (HEA) Research"
permalink: /hea/
description: "Detailed information about High Entropy Alloys research including methodologies, code implementations, and results."
---

<div class="content-container">
  <div class="two-column-layout">

    <!-- Left Column - Details and Descriptions -->
    <div class="left-column">

      <h3>Methodology</h3>
      <ul>
        <li><strong>Initial Structure:</strong> BCC structure prepared with Python and LAMMPS</li>
        <li><strong>Alloy Processing:</strong> Applied shear flow during quenching from 3000 K to 300 K under NVT ensemble</li>
        <li><strong>Microstructural Analysis:</strong> Used Common Neighbor Analysis (CNA), Polyhedral Template Maping (PTM), Grain Segmentation to identify differnt phase and observe microstructure</li>
        <li><strong>Mechanical Properties:</strong> Conducted uniaxial tensile simulations to determine stress–strain behavior at various emperature (300 -1200 K)</li>
        <li><strong>Dislocation Dynamics:</strong> Applied DXA to study evoluation of various dislocations</li>
        <li><strong>Chemical Ordering:</strong> Computed Warren–Cowley CSRO parameters</li> 
        <li><strong>Radiation Damage:</strong> Simulated PKA to observe radiation damage tolerance</li> 
         <li><strong>Nanoindentation:</strong> Performed indentation and retraction to evaluate hardness and subsurface plasticity</li>                
      </ul>

      <h3>Key Findings</h3>
      <p>Study demonstrated that shear-processed HEAs exhibit:</p>
      <ul>
        <li>Finer, equiaxed nanocrystalline grain structures</li>
        <li>More stable dislocation motion with fewer entanglements</li>
        <li>Enhanced strength–ductility balance</li>
        <li>Greater thermal stability across high-temperature range</li>
        <li>Strengthening via TWIP and TRIP mechanisms</li>
        <li>Intensified Al–Fe and Al–Co chemical short-range ordering</li>
      </ul>

      <h3>Applications</h3>
      <p>Potential applications of these HEAs include:</p>
      <ul>
        <li>Aerospace components</li>
        <li>High-temperature structural parts</li>
        <li>Nuclear reactor materials</li>
        <li>Advanced Manufacturing</li>
      </ul>

      <h3>Future Work</h3>
      <p>Future research directions include optimization of processing parameters and exploration of new alloy systems.</p>

    </div>

    <!-- Right Column - Code and Images -->
    <div class="right-column">
      
      <h2>Code Implementation</h2>
      
      <h3>Initial Structure</h3>
      <div class="code-block">
        <pre><code class="language-python">
import numpy as np
import random

# HEA composition
composition = {
    'Al': 6.977,
    'Fe': 23.256,
    'Ni': 23.256,
    'Cr': 23.256,
    'Co': 23.256
}

# Output file name
output_filename = "alloy.in"

# Box size (90 nm cube)
box_size_nm = 2.0
box_size_angstrom = box_size_nm * 10.0

# FCC lattice parameter (approximate average)
lattice_param = 3.6
atoms_per_cell = 4

# Number of FCC unit cells per side
cells_per_side = int(box_size_angstrom / lattice_param)
total_cells = cells_per_side ** 3
total_atoms = total_cells * atoms_per_cell

# Distribute atom types
elements = []
for elem, perc in composition.items():
    count = int(round((perc / 100) * total_atoms))
    elements.extend([elem] * count)
while len(elements) < total_atoms:
    elements.append(random.choice(list(composition.keys())))
random.shuffle(elements)

# FCC basis
fcc_basis = np.array([
    [0.0, 0.0, 0.0],
    [0.5, 0.5, 0.0],
    [0.5, 0.0, 0.5],
    [0.0, 0.5, 0.5]
])

# Generate atom positions
positions = []
for i in range(cells_per_side):
    for j in range(cells_per_side):
        for k in range(cells_per_side):
            origin = np.array([i, j, k]) * lattice_param
            for basis in fcc_basis:
                pos = origin + basis * lattice_param
                positions.append(pos)
positions = np.array(positions[:total_atoms])

# Create data file
type_map = {elem: idx + 1 for idx, elem in enumerate(composition.keys())}
masses = {'Al': 26.9815, 'Fe': 55.845, 'Ni': 58.6934, 'Cr': 51.9961, 'Co': 58.9332}

with open(output_filename, 'w') as f:
    f.write("LAMMPS data file for HEA in 90nm box\n\n")
    f.write(f"{total_atoms} atoms\n")
    f.write(f"{len(composition)} atom types\n\n")
    f.write(f"0.0 {box_size_angstrom:.6f} xlo xhi\n")
    f.write(f"0.0 {box_size_angstrom:.6f} ylo yhi\n")
    f.write(f"0.0 {box_size_angstrom:.6f} zlo zhi\n\n")
    f.write("Masses\n\n")
    for elem, idx in type_map.items():
        f.write(f"{idx} {masses[elem]} # {elem}\n")
    f.write("\nAtoms\n\n")
    for atom_id, (elem, pos) in enumerate(zip(elements, positions), start=1):
        f.write(f"{atom_id} {type_map[elem]} {pos[0]:.6f} {pos[1]:.6f} {pos[2]:.6f}\n")

print(f"✅ HEA structure written to {output_filename}")
        </code></pre>
      </div>

      <h3>LAMMPS Input Script</h3>
      <div class="code-block">
        <pre><code class="language-lammps">
        log log_file.txt

# ------------------------ INITIALIZATION ----------------------------
units       metal
dimension   3
boundary    p p p
atom_style  atomic

package gpu 1
neighbor    2.0 bin
neigh_modify every 1 delay 0 check yes

# ------------------------ READ ATOMIC STRUCTURE ---------------------
read_data hea_Al_0.3.data

# Define interatomic potential
pair_style eam/alloy/gpu
pair_coeff * * FeCrCoNiAl.setfl Al Fe Ni Cr Co

# ------------------------ MINIMIZATION -----------------------------
reset_timestep 0
timestep 0.001  # 1 fs
min_style fire
minimize 1e-6 1e-8 1000 10000

# ------------------------ EQUILIBRATION @300K -----------------------------
velocity all create 300 12345 mom yes rot no
fix eq1 all npt temp 300 300 1 iso 0 0 1 drag 1
thermo 1000
run 100000  # 100 ps
unfix eq1
write_data Pre_melt_structure.data

# ------------------------ MELTING @3000K -----------------------------
dump pre all custom 1000 dump.pre_tensile.txt id type x y z vx vy vz
dump_modify pre element Al Fe Ni Cr Co

fix melt all npt temp 300 3000 1 iso 0 0 1 drag 1
run 305000  # 50 ps at 3000K
unfix melt

velocity all scale 3000
fix hold all npt temp 3000 3000 1 iso 0 0 1 drag 1
run 30000  # 50 ps at 3000K
unfix hold

# ------------------------ SHEAR FLOW SETUP FOR SAMPLE A -----------------------------
velocity all ramp vx 0.0 2.0 y 0 90 sum yes
velocity all ramp vy 0.0 2.0 x 0 90 sum yes

# ------------------------ COOLING  -----------------------------

variable tdamp equal 1.0
fix cool all npt temp 3000 300 ${tdamp} iso 0 0 ${tdamp} drag 2

restart 500000 restart.cooling.*

run 10800000
unfix cool
write_data annealed_structure_sample_A.data

# ------------------------ FINAL EQUILIBRATION @300K -----------------------------
velocity all scale 300
fix final_eq all npt temp 300 300 1 iso 0 0 1 drag 1
run 50000  # 30 ps
unfix final_eq
undump pre

variable tmp equal "lx"
variable L0 equal ${tmp}
print "Initial Length, L0: ${L0}"

# ------------------------ TENSILE TEST -----------------------------
reset_timestep 0
fix 1 all nve

variable srate equal 3.0e9
variable srate1 equal "v_srate/1.0e12"
fix 2 all deform 1 x erate ${srate1} units box remap x

variable strain equal "(lx-v_L0)/v_L0"
variable p1 equal "v_strain"
variable p2 equal "-pxx/10000"
variable p3 equal "-pyy/10000"
variable p4 equal "-pzz/10000"
fix def1 all print 100 "${p1} ${p2} ${p3} ${p4}" file Al_HEA.def1.txt screen no

dump 1 all custom 1000 dump.tensile.txt id type x y z vx vy vz
dump_modify 1 element Al Fe Ni Cr Co append yes

thermo 1000
thermo_style custom step v_strain temp v_p2 v_p3 v_p4 ke pe press
run 70000  # ~70 ps of tensile strain

print "All done"
        </code></pre>
      </div>

      <h3>Results Visualization</h3>
      
      <figure>
        <img src="{{ site.baseurl }}/assets/images/hea_microstructure.png" alt="HEA Microstructure">
        <figcaption class="center-caption">Figure 1: Typical microstructure of developed HEA</figcaption>
      </figure>

      <figure>
        <img src="{{ site.baseurl }}/assets/images/phase_diagram.png" alt="Phase Diagram">
        <figcaption class="center-caption">Figure 2: Calculated phase diagram for the HEA system</figcaption>
      </figure>

      <h3>Data Analysis Script</h3>
      <div class="code-block">
        <pre><code class="language-python">
import pandas as pd
import matplotlib.pyplot as plt

def plot_mechanical_properties(data_file):
    """
    Plot mechanical properties of different HEA compositions
    """
    data = pd.read_csv(data_file)
    
    fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 5))
    
    # Yield strength vs composition
    ax1.scatter(data['composition'], data['yield_strength'])
    ax1.set_xlabel('Composition')
    ax1.set_ylabel('Yield Strength (MPa)')
    
    # Hardness vs composition
    ax2.scatter(data['composition'], data['hardness'])
    ax2.set_xlabel('Composition')
    ax2.set_ylabel('Hardness (HV)')
    
    plt.tight_layout()
    plt.savefig('mechanical_properties.png', dpi=300)
    plt.show()
        </code></pre>
      </div>

    </div>

  </div>

  <!-- Additional Resources Section -->
  <div class="additional-resources">
    <h2>Additional Resources</h2>
    <ul>
      <li><a href="{{ site.baseurl }}/assets/documents/hea_publication.pdf">Download Full Paper (PDF)</a></li>
      <li><a href="https://github.com/yourusername/hea-research">GitHub Repository</a></li>
      <li><a href="{{ site.baseurl }}/research/">Back to Research Overview</a></li>
    </ul>
  </div>
</div>

<style>
.content-container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 20px;
}

.two-column-layout {
  display: flex;
  gap: 30px;
  flex-wrap: wrap;
  line-height: 1.6;
}

.left-column, .right-column {
  flex: 1;
  min-width: 300px;
}

.left-column h2, .right-column h2 {
  color: #2c3e50;
  border-bottom: 2px solid #3498db;
  padding-bottom: 5px;
}

.left-column h3, .right-column h3 {
  color: #34495e;
  margin-top: 25px;
}

.left-column ul {
  padding-left: 20px;
}

.left-column li {
  margin-bottom: 8px;
}

.code-block {
  background: #f6f8fa;
  padding: 15px;
  border-radius: 5px;
  margin-bottom: 20px;
  overflow-x: auto;
}

.code-block pre code {
  font-size: 0.7em;
  line-height: 1.4;
  font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
}

figure {
  margin: 20px 0;
  text-align: center;
}

figure img {
  width: 100%;
  border-radius: 5px;
  max-width: 100%;
}

.center-caption {
  text-align: center;
  font-style: italic;
  margin-top: 8px;
  color: #666;
  display: block;
}

.additional-resources {
  margin-top: 40px;
  padding-top: 20px;
  border-top: 1px solid #eee;
}

.additional-resources ul {
  padding-left: 20px;
}

.additional-resources li {
  margin-bottom: 10px;
}

/* Responsive design */
@media (max-width: 768px) {
  .content-container {
    padding: 0 20px;
  }
  
  .two-column-layout {
    gap: 20px;
  }
}
</style>