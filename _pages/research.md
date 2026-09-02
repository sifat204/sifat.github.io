---
layout: archive
title: ""
permalink: /research/
author_profile: true
---
## Master's Thesis
**Molecular Dynamics Study of Shear-Assisted Microstructural Evolution and Property Response in Al<sub>0.3</sub>CoCrFeNi High-Entropy Alloy**<br>
**Tools:** LAMMPS, OVITO, Python, VESTA  
**Keywords:** Molecular Dynamics, High-Entropy Alloys, Grain Refinement, Dislocation Mechanics, Radiation Damage

<ul style="text-align: justify;">
  <li>Investigated how shear-assisted solidification modifies the microstructure and performance of Al<sub>0.3</sub>CoCrFeNi high-entropy alloys using molecular dynamics simulations.</li>

  <li>Examined the evolution of grain structure, planar faults, dislocations, and chemical short-range ordering under different solidification conditions.</li>

  <li>Evaluated tensile strength, ductility, deformation mechanisms, and thermal stability to establish processing–microstructure–property relationships.</li>

  <li>Assessed the response of the processed microstructures under cyclic loading to compare their fatigue stability and defect-evolution behavior.</li>

  <li>Investigated 5 keV displacement cascades to quantify radiation-induced defect generation, spatial defect distributions, defect recovery, and the post-irradiation mechanical response.</li>

  <li>Demonstrated that different interface architectures provide distinct advantages under tensile, cyclic, and irradiation conditions, highlighting the potential of processing-controlled microstructure design for demanding structural applications.</li>
</ul>

<!-- ===================== -->
<!-- Row 1: Figures (a-d) -->
<!-- ===================== -->

<div style="
  display: flex;
  gap: 12px;
  justify-content: center;
  align-items: flex-start;
  flex-wrap: wrap;
  margin-bottom: 25px;
">

  <!-- (a) -->
  <figure style="width: 23%; min-width: 170px; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/Masters/Sample_A_CNA.png"
         alt="CNA analysis of Sample A"
         style="width: 100%; height: auto;">
    <figcaption class="center-caption" style="text-align: center;">
      (a) CNA analysis of Sample A
    </figcaption>
  </figure>

  <!-- (b) -->
  <figure style="width: 23%; min-width: 170px; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/Masters/sample_A_planar_faults_defect_only_refined.png"
         alt="Planar faults in Sample A"
         style="width: 100%; height: auto;">
    <figcaption class="center-caption" style="text-align: center;">
      (b) Planar-fault structure of Sample A
    </figcaption>
  </figure>

  <!-- (c) -->
  <figure style="width: 23%; min-width: 170px; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/Masters/Sample_B_CNA.png"
         alt="CNA analysis of Sample B"
         style="width: 100%; height: auto;">
    <figcaption class="center-caption" style="text-align: center;">
      (c) CNA analysis of Sample B
    </figcaption>
  </figure>

  <!-- (d) -->
  <figure style="width: 23%; min-width: 170px; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/Masters/sample_B_planar_faults_defect_only_refined.png"
         alt="Planar faults in Sample B"
         style="width: 100%; height: auto;">
    <figcaption class="center-caption" style="text-align: center;">
      (d) Planar-fault structure of Sample B
    </figcaption>
  </figure>

</div>

<!-- ===================== -->
<!-- Row 2: Figures (e-f) -->
<!-- ===================== -->

<div style="
  display: flex;
  gap: 25px;
  justify-content: center;
  align-items: flex-start;
  flex-wrap: wrap;
">

  <!-- (e) -->
  <figure style="width: 45%; min-width: 280px; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/Masters/fp_evolution_vs_time.png"
         alt="Frenkel-pair evolution at 5 keV"
         style="width: 100%; height: auto;">
    <figcaption class="center-caption" style="text-align: center;">
      (e) Frenkel-pair evolution at 5 keV
    </figcaption>
  </figure>

  <!-- (f) -->
  <figure style="width: 45%; min-width: 280px; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/Masters/ws_pairs_AB.png"
         alt="Wigner-Seitz defect sites in Samples A and B"
         style="width: 100%; height: auto;">
    <figcaption class="center-caption" style="text-align: center;">
      (f) Wigner-Seitz defect sites in Samples A and B
    </figcaption>
  </figure>

</div>

<p style="text-align: justify;"><em>This project marks a key milestone in my research development, combining atomic-scale modeling, mechanical property analysis, and radiation damage simulation to address complex challenges in HEA design. It also laid the groundwork for my doctoral research direction.</em></p>
*For more details and resources* <a href="{{ site.baseurl }}/hea/" style="display: inline-block; padding: 8px 16px; background-color: #007cba; color: white; text-decoration: none; border-radius: 4px;">click here</a>

## LAMMPS-based Molecular Dynamics Projects 
**1. WMoZrTiTa Refractory High Entropy Alloy (RHEA)**
<ul style="text-align: justify;">
  <li>Performed hybrid Monte Carlo/Molecular Dynamics (MC/MD) simulations to investigate microstructural evolution and mechanical properties of the WMoZrTiTa RHEA.</li>

  <li>Investigated the influence of chemical short-range order (CSRO) on the mechanical response and underlying deformation mechanisms.</li>

  <li>Performed radiation-damage simulations using Primary Knock-on Atom (PKA) collision cascades to evaluate irradiation-induced defect evolution.</li>
</ul>

<div style="display: flex; gap: 20px; flex-wrap: wrap; justify-content: center; align-items: flex-start;">

  <figure style="width: 45%; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/Structuer_MC-MD.png" alt="MC/MD Hybid Study" style="width: 100%;">
    <figcaption class="center-caption">(a) Final structure after 6M MC/MD hybrid study</figcaption>
  </figure>

  <figure style="width: 45%; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/potential_energy_full_5M_6M_maroon_darkblue.png" alt="Potential Energy vs timestep" style="width: 100%;">
    <figcaption class="center-caption">(b) Potential energy convergence during MC/MD hybrid simulation</figcaption>
  </figure>

</div>

**Zr–Nb Alloy**
<ul style="text-align: justify;">
  <li>Investigated the influence of Nb content on the high-temperature mechanical performance of Zr–Nb alloys using atomistic simulations.</li>

  <li>Performed simulated annealing and tensile loading simulations to evaluate creep resistance, strength, and dislocation evolution.</li>

  <li>Analyzed dislocation dynamics to understand the deformation mechanisms associated with different Nb concentrations.</li>

  <li>Performed nanoindentation simulations to investigate hardness response and subsurface shear localization.</li>

  <li>Provided atomistic insights into the optimization of Zr–Nb alloys for potential nuclear and structural applications.</li>
</ul>

<div style="display: flex; gap: 20px; flex-wrap: wrap; justify-content: center; align-items: flex-start;">

  <figure style="width: 45%; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/zrnb.png" alt="BCC Initial Structure" style="width: 100%;">
    <figcaption class="center-caption">(a) Initial BCC Structure</figcaption>
  </figure>

  <figure style="width: 45%; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/zrnb_final.png" alt="Solidified Structure" style="width: 100%;">
    <figcaption class="center-caption">(b) Microstructure after rapid solidification</figcaption>
  </figure>

</div>

**Transition Metal Dichalcogenides (TMDs)**
<ul style="text-align: justify;">
  <li>Investigated the mechanical behavior of pristine and defected monolayer WSe₂ using structures prepared with VESTA and ATOMSK and simulated in LAMMPS.</li>

  <li>Performed tensile simulations at room and elevated temperatures to evaluate stress–strain response and temperature-dependent mechanical behavior.</li>

  <li>Analyzed crack propagation and atomic-scale failure mechanisms to understand the fracture characteristics of defected WSe₂ monolayers.</li>

  <li>Performed nanoindentation simulations to assess surface hardness and local deformation behavior.</li>

  <li>Provided atomistic insights into the suitability of monolayer WSe₂ for flexible electronics and nanomechanical applications.</li>
</ul>

<div style="display: flex; gap: 20px; flex-wrap: wrap; justify-content: center; align-items: flex-start;">

  <figure style="width: 45%; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/TMD_pit.PNG" alt="Defected Monolayer" style="width: 100%;">
    <figcaption class="center-caption">(a) Defected Monolayer</figcaption>
  </figure>

  <figure style="width: 45%; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/TMD_SS.PNG" alt="Solidified Structure" style="width: 100%;">
    <figcaption class="center-caption">(b) Stress-Strain Profile at Room Temperature</figcaption>
  </figure>

</div>

## Undergrade Projects 
**Thesis: Design and Evolution of a Novel Solar Biomass Hybrid Dryer**
<ul style="text-align: justify;">
  <li>Designed and fabricated a solar–biomass hybrid dryer following a detailed engineering design and development process.</li>

  <li>Evaluated the energy and exergy performance of the dryer under three operating modes: solar, biomass, and hybrid drying.</li>

  <li>Compared the thermodynamic performance of the three drying modes and found the hybrid mode to provide the highest overall efficiency.</li>

  <li>Conducted drying experiments using three different cabbage loadings: 8 kg, 10 kg, and 12 kg.</li>

  <li>Assessed the quality of the dried cabbage samples to evaluate the effectiveness of the developed drying system.</li>
</ul>

<div style="display: flex; gap: 20px; flex-wrap: wrap; justify-content: center; align-items: flex-start;">

  <figure style="width: 45%; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/Undergrade/Dryer.png" alt="Experimental Set up" style="width: 100%;">
    <figcaption class="center-caption">(a) Experimental Set up</figcaption>
  </figure>

  <figure style="width: 45%; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/Undergrade/Dryer_1.png" alt="Moisture Removal Rate at different drying configuration" style="width: 100%;">
    <figcaption class="center-caption">(b) Moisture Removal Rate at different drying configuration</figcaption>
  </figure>

</div>

**Applied Thermodynamics Project: Enhancement of thermal power plant performance through solar-assisted feed water heaters: An innovative repowering approach**
<ul style="text-align: justify;">
  <li>Investigated the energy and exergy optimization of a thermal power plant based on a regenerative Rankine cycle integrated with solar-powered feedwater heating.</li>

  <li>Modeled a 200 MW unit of the Shahid Montazeri Power Plant and evaluated different feedwater-heater configurations using EES.</li>

  <li>Analyzed 14 design scenarios to compare the thermodynamic performance of alternative regenerative configurations.</li>

  <li>Performed parametric studies to investigate the effects of steam temperature and pressure on net power output, energy efficiency, and exergy efficiency.</li>

  <li>Identified an optimized configuration that improved net power generation as well as the overall energy and exergy performance of the plant.</li>

  <li>Highlighted the potential of integrating solar thermal energy with conventional large-scale power plants to enhance overall system performance.</li>
</ul>

<div style="display: flex; gap: 20px; flex-wrap: wrap; justify-content: center; align-items: flex-start;">

  <figure style="width: 45%; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/Undergrade/Review Schematic .png" alt="Schedmatic Diagram of the Power plant" style="width: 100%;">
    <figcaption class="center-caption">(a) Schematic Diagram of the Pwoer Plant</figcaption>
  </figure>

  <figure style="width: 45%; margin: 0;">
    <img src="{{ site.baseurl }}/assets/images/Undergrade/Exergy.png" alt="Exergy Distruction" style="width: 100%;">
    <figcaption class="center-caption">(b) Exergy Destruction of system</figcaption>
  </figure>

</div>