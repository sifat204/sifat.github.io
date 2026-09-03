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
        <p><strong>Molecular Dynamics Study of Shear-Assisted Microstructural Evolution and Property Response in Al<sub>0.3</sub>CoCrFeNi High-Entropy Alloy</strong></p>
<h3>Methodology</h3>
<ul>
  <li><strong>Initial Structure:</strong> BCC structure prepared with Python and LAMMPS</li>
  <li><strong>Alloy Processing:</strong> Applied shear flow during quenching from 3000 K to 300 K under NVT ensemble</li>
  <li><strong>Microstructural Analysis:</strong> Used Common Neighbor Analysis (CNA), Polyhedral Template Matching (PTM), and Grain Segmentation to identify different phases and observe microstructure</li>
  <li><strong>Mechanical Properties:</strong> Conducted uniaxial tensile simulations to determine stress–strain behavior at various temperatures (300-1200 K)</li>
  <li><strong>Dislocation Dynamics:</strong> Applied DXA to study the evolution of various dislocations</li>
  <li><strong>Chemical Ordering:</strong> Computed Warren-Cowley CSRO parameters</li>
  <li><strong>Radiation Damage:</strong> Simulated primary knock-on atom (PKA) cascades at 5Kev to evaluate radiation damage tolerance across differently processed microstructures</li>
  <li><strong>Low-Cycle Fatigue:</strong> Applied cyclic loading at different temperatures to study low-cycle fatigue tolerance</li>
</ul>
<h3>Key Findings</h3>
<p>Study demonstrated that shear-processed HEAs exhibit:</p>
<ul>
  <li>Finer, equiaxed nanocrystalline grain structures</li>
  <li>More stable dislocation motion with fewer entanglements</li>
  <li>Enhanced strength-ductility balance</li>
  <li>Greater thermal stability across the high-temperature range</li>
  <li>Strengthening via TWIP and TRIP mechanisms</li>
  <li>Intensified Al-Fe and Al-Co chemical short-range ordering</li>
  <li>Radiation tolerance strongly dependent on processing condition, with distinct microstructural variants showing markedly different resistance to cumulative cascade damage</li>
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
<p>Future work includes extending radiation damage analysis beyond single-cascade events to a two-stage MC/MD multicascade framework using kinetic Monte Carlo to capture defect relaxation between successive cascades and applying this approach to new alloy systems currently under investigation.</p>
      <h3>Hybrid MC/MD Simulation</h3>
      <p style="text-align: justify;">Hybrid MC/MD simulation generates thermally equilibrated alloy structures by combining two techniques. Short Molecular Dynamics (MD) bursts relax atomic positions, then Monte Carlo (MC) proposes atom swaps to sample chemical configurations. The energy change after MD relaxation determines if a swap is accepted. This process efficiently explores the system's structural and chemical landscape to study properties like chemical short-range order (CSRO) and phase stability.</p>
      <p style="text-align: justify;"> This interesting process has been explored in this project. The atomic structure and radial distribution function; g(r) shows checmical ordering after MC/MD hybrid simulation </p>
      <div style="display: flex; gap: 20px; flex-wrap: wrap; justify-content: center; align-items: flex-start;">
  <figure style="width: 45%; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/mcmd.png" alt="Final Structure" style="width: 100%;">
    <figcaption style="
  text-align: center !important;
  width: 100%;
  font-style: italic;
">(a) Final Structure after MC/MD simulation</figcaption>
  </figure>
  <figure style="width: 45%; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/random.png" alt="Initial Structure" style="width: 100%;">
    <figcaption style="
  text-align: center !important;
  width: 100%;
  font-style: italic;
">(b) Initial Structure</figcaption>
  </figure>
</div>
      <figure>
        <img src="{{ site.baseurl }}/assets/images/mcmdgf.png" alt="gr function A" style="width: 100%;">
        <figcaption style="
  text-align: center !important;
  width: 100%;
  font-style: italic;
">(c) Radial Distribution Fuction of Sample A: After MC/MD </figcaption>
      </figure>
      <figure>
        <img src="{{ site.baseurl }}/assets/images/rangf.png" alt="gf fucntion B" style="width: 100%;">
        <figcaption style="
  text-align: center !important;
  width: 100%;
  font-style: italic;
">(d) Radial Distribution Fuction of Initial Structure</figcaption>
      </figure>
      <h3>Results Visualization</h3>     
      <figure>
        <img src="{{ site.baseurl }}/assets/images/stress.png" alt="Stress-Strain Curve">
        <figcaption style="
  text-align: center !important;
  width: 100%;
  font-style: italic;
">Figure 1: Stress-Strain Curve for Sample A and B</figcaption>
      </figure>
      <figure>
        <img src="{{ site.baseurl }}/assets/images/Sample A_A7.png" alt="Grain Segmentation A">
        <figcaption style="
  text-align: center !important;
  width: 100%;
  font-style: italic;
">Figure 2: Grain Segmentation in Sample A</figcaption>
      </figure>
      <figure>
        <img src="{{ site.baseurl }}/assets/images/Sample B_B7.png" alt="Grain Segmentation B">
        <figcaption style="
  text-align: center !important;
  width: 100%;
  font-style: italic;
">Figure 3: Grain Segmentation in Sample B</figcaption>
      </figure>
    </div>

<!-- Right Column - Code and Images -->
    <div class="right-column">

      <h2>Code Implementation</h2>
      <p style="font-size: 0.9em;">
        Full repository:
        <a href="https://github.com/sifat204/LAMMPS-Codes" target="_blank" style="color: #007cba; text-decoration: none;">github.com/sifat204/LAMMPS-Codes →</a>
      </p>

      <div class="code-link-grid">
        <a class="code-card" href="https://github.com/sifat204/LAMMPS-Codes/blob/main/Structure_Python.txt" target="_blank">
          <h4>Initial Structure Generation</h4>
          <p>Python script for building the initial HEA structure and generating the LAMMPS data file.</p>
        </a>
        <a class="code-card" href="https://github.com/sifat204/LAMMPS-Codes/blob/main/LAMMPS-Solidified%20Structure.txt" target="_blank">
          <h4>Tensile Test Simulation</h4>
          <p>LAMMPS script for prepaing microstructure and uniaxial tensile testing at 300 K temperature.</p>
        </a>
      </div>

      <h3>Featured: MC/MD Hybrid Simulation</h3>
      <div class="code-block">
        <details open>
          <summary>View full script</summary>
          <pre><code class="language-lammps">
# Hybrid MC/MD simulation for Al-Fe-Ni-Cr-Co HEA
# Combines continuous MD (NVT integration) with periodic Monte Carlo
# atom-swap moves to sample chemical ordering (CSRO) at fixed T.
#----- Note ----
# Requires LAMMPS built with the MC package (needed for atom/swap).

log MC_log_file.txt
units metal
atom_style atomic
dimension 3
boundary p p p

package gpu 1
neighbor 2.0 bin
neigh_modify every 1 delay 0 check yes

# ---- STRUCTURE ----
read_data test_st.data

# ---- POTENTIAL ----
# Note: GPU acceleration here applies to the pair style / neighbor list.
# The integrator fixes below (nvt, npt) intentionally do not use /gpu
# suffixes, since GPU offload mainly benefits pairwise force evaluation.
pair_style eam/alloy/gpu
pair_coeff * * FeCrCoNiAl.setfl Al Fe Ni Cr Co

# ---- ENERGY MINIMIZATION ----
minimize 1.0e-5 1.0e-7 5000 10000
reset_timestep 0

# ---- INITIAL EQUILIBRATION @ 1000 K ----
timestep 0.002
velocity all create 1000.0 12345 rot yes dist gaussian
fix nvt all nvt temp 1000.0 1000.0 0.1
thermo 1000
run 50000  # 100 ps equilibration
unfix nvt

# ---- HYBRID MC/MD PRODUCTION RUN ----
# The nvt_prod fix provides continuous MD integration; the atom/swap
# fixes below perform periodic MC moves on top of it. Running both
# together (rather than alternating) is the standard LAMMPS pattern
# for hybrid MC+MD, per the fix atom/swap documentation.
fix nvt_prod all nvt temp 1000.0 1000.0 0.1

# ---- MONTE CARLO SETUP (Canonical Ensemble) ----
# Atom type mapping: 1=Al, 2=Fe, 3=Ni, 4=Cr, 5=Co
# fix atom/swap only swaps between the two types listed per instance,
# so four fixes are chained (Al-Fe, Fe-Ni, Ni-Cr, Cr-Co) to allow
# composition sampling across all five elements. Non-adjacent pairs
# (e.g. Al-Co) are sampled indirectly through this chain over the
# course of the run, rather than swapped directly.
fix swap1 all atom/swap 100 10 12345 1000.0 types 1 2
fix swap2 all atom/swap 100 10 12346 1000.0 types 2 3
fix swap3 all atom/swap 100 10 12347 1000.0 types 3 4
fix swap4 all atom/swap 100 10 12348 1000.0 types 4 5

# ---- COMPOSITION MONITORING ----
# typecounts returns one count per atom type (Al, Fe, Ni, Cr, Co, in
# that order) -- not just Al, despite the shorter name below.
compute typecounts all count/type atom
fix composition all ave/time 100 50 5000 &
    c_typecounts[1] c_typecounts[2] c_typecounts[3] c_typecounts[4] c_typecounts[5] &
    file composition.txt

# ---- OUTPUT SETTINGS ----
# f_swapN[1] = cumulative attempted swaps, f_swapN[2] = cumulative
# accepted swaps for that fix (only swap1/swap2 shown here for brevity;
# add f_swap3[*] and f_swap4[*] if you want full acceptance stats).
thermo 1000
thermo_style custom step temp pe etotal press vol f_swap1[1] f_swap1[2] f_swap2[1] f_swap2[2]
thermo_modify flush yes

# Periodic restart files in case the run needs to be resumed
restart 50000 restart.mc.*

run 600000  # 1200 ps hybrid MC/MD hold at 1000 K

unfix swap1
unfix swap2
unfix swap3
unfix swap4

# ---- COOLING RAMP: 1000 K -> 300 K ----
unfix nvt_prod
fix nvt all nvt temp 1000.0 300.0 0.1
thermo_style custom step temp pe etotal press vol
run 400000  # ~0.8 ns cool
unfix nvt

# ---- FINAL HOLD @ 300 K (NPT) ----
fix npt all npt temp 300.0 300.0 0.1 iso 0.0 0.0 1.0
run 50000  # 0.4 ns hold
unfix npt

# ---- OUTPUT FINAL STRUCTURE ----
write_data final_st.data
          </code></pre>
        </details>
      </div>
      <p style="font-size: 0.9em;">
        <a href="https://github.com/sifat204/LAMMPS-Codes/blob/main/MC_MD%20Hybrid%20LAMMPS.txt" target="_blank" style="color: #007cba; text-decoration: none;">View on GitHub →</a>
      </p>
      <p style="font-size: 0.9em; color: #666;"><em><strong>Additional simulation code (shear-assisted processing, radiation damage and low cycle fatigue test) will be released following publication of the associated manuscript.</strong></em></p>

    </div>

  </div>

  <!-- Additional Resources Section -->
  <div class="additional-resources">
    <ul>
      <!-- <li><a href="{{ site.baseurl }}/assets/documents/hea_publication.pdf">Download Full Paper (PDF)</a></li> -->
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
  /* color: #000000fb; */
  border-bottom: 2px solid #3498db;
  padding-bottom: 5px;
}

.left-column h3, .right-column h3 {
  /* color: #000000ff; */
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
  padding: 7px;
  border-radius: 5px;
  margin-bottom: 15px;
  overflow-x: auto;
}

.code-block pre code {
  font-size: 0.7em;
  line-height: 1;
  font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
}

.code-block summary {
  cursor: pointer;
  font-weight: 600;
  padding: 4px 0;
}

.code-link-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1rem;
  margin: 1rem 0;
}

.code-card {
  display: block;
  padding: 1rem;
  border: 1px solid #ddd;
  border-radius: 8px;
  text-decoration: none;
  color: inherit;
  transition: box-shadow 0.15s ease;
}

.code-card:hover {
  box-shadow: 0 2px 8px rgba(0,0,0,0.08);
}

.code-card h4 {
  margin: 0 0 0.4rem 0;
  color: #007cba;
}

.code-card p {
  margin: 0;
  font-size: 0.85em;
  color: #555;
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
  /* color: #030000ec; */
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