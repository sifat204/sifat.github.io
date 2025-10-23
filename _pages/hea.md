---
layout: archive
title: "High Entropy Alloys (HEA) Research"
permalink: /hea/
description: "Detailed information about High Entropy Alloys research including methodologies, code implementations, and results."
---

<div class="two-column-layout" style="display: flex; gap: 30px; flex-wrap: wrap;">

  <!-- Left Column - Details and Descriptions -->
  <div class="left-column" style="flex: 1; min-width: 300px;">
    
    <h2>Research Overview</h2>
    <p>This research focuses on the development and characterization of High Entropy Alloys (HEAs) with exceptional mechanical properties and thermal stability.</p>

    <h3>Methodology</h3>
    <ul>
      <li><strong>Alloy Design:</strong> Multi-principal element approach</li>
      <li><strong>Fabrication:</strong> Arc melting under argon atmosphere</li>
      <li><strong>Characterization:</strong> XRD, SEM, TEM analysis</li>
      <li><strong>Testing:</strong> Mechanical and thermal properties evaluation</li>
    </ul>

    <h3>Key Findings</h3>
    <p>Our research has demonstrated that HEAs exhibit:</p>
    <ul>
      <li>Superior strength-to-weight ratios</li>
      <li>Excellent corrosion resistance</li>
      <li>Enhanced thermal stability</li>
      <li>Unique deformation mechanisms</li>
    </ul>

    <h3>Applications</h3>
    <p>Potential applications of these HEAs include:</p>
    <ul>
      <li>Aerospace components</li>
      <li>High-temperature tools</li>
      <li>Nuclear reactors</li>
      <li>Marine engineering</li>
    </ul>

    <h3>Future Work</h3>
    <p>Future research directions include optimization of processing parameters and exploration of new alloy systems.</p>

  </div>

  <!-- Right Column - Code and Images -->
  <div class="right-column" style="flex: 1; min-width: 300px;">
    
    <h2>Code Implementation</h2>
    
    <h3>Phase Prediction Algorithm</h3>
    <div style="background: #f6f8fa; padding: 15px; border-radius: 5px; margin-bottom: 20px;">
      <pre><code class="language-python">
import numpy as np
from sklearn.ensemble import RandomForestClassifier

def predict_phase_stability(composition, features):
    """
    Predict phase stability of HEA compositions
    """
    model = RandomForestClassifier(n_estimators=100)
    model.fit(features, composition['phase'])
    predictions = model.predict(composition['test_features'])
    return predictions

# Example usage
composition_data = load_composition_data()
stability_predictions = predict_phase_stability(composition_data)
      </code></pre>
    </div>

    <h3>Microstructure Analysis</h3>
    <div style="background: #f6f8fa; padding: 15px; border-radius: 5px; margin-bottom: 20px;">
      <pre><code class="language-matlab">
% MATLAB code for microstructure analysis
function [grain_size, phase_fraction] = analyze_microstructure(image_path)
    % Load and preprocess image
    img = imread(image_path);
    img_gray = rgb2gray(img);
    
    % Grain boundary detection
    edges = edge(img_gray, 'canny');
    
    % Calculate grain size distribution
    stats = regionprops(edges, 'Area');
    grain_size = mean([stats.Area]);
    
    % Phase fraction calculation
    phase_fraction = calculate_phase_fraction(img);
end
      </code></pre>
    </div>

    <h3>Results Visualization</h3>
    
    <figure style="margin: 20px 0;">
      <img src="{{ site.baseurl }}/assets/images/hea_microstructure.png" alt="HEA Microstructure" style="width: 100%; border-radius: 5px;">
      <figcaption class="center-caption">Figure 1: Typical microstructure of developed HEA</figcaption>
    </figure>

    <figure style="margin: 20px 0;">
      <img src="{{ site.baseurl }}/assets/images/phase_diagram.png" alt="Phase Diagram" style="width: 100%; border-radius: 5px;">
      <figcaption class="center-caption">Figure 2: Calculated phase diagram for the HEA system</figcaption>
    </figure>

    <h3>Data Analysis Script</h3>
    <div style="background: #f6f8fa; padding: 15px; border-radius: 5px;">
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
<div style="margin-top: 40px; padding-top: 20px; border-top: 1px solid #eee;">
  <h2>Additional Resources</h2>
  <ul>
    <li><a href="{{ site.baseurl }}/assets/documents/hea_publication.pdf">Download Full Paper (PDF)</a></li>
    <li><a href="https://github.com/yourusername/hea-research">GitHub Repository</a></li>
    <li><a href="{{ site.baseurl }}/research/">Back to Research Overview</a></li>
  </ul>
</div>

<style>
.two-column-layout {
  line-height: 1.6;
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

pre code {
  font-size: 0.9em;
  line-height: 1.4;
}

.center-caption {
  text-align: center;
  font-style: italic;
  margin-top: 8px;
  color: #666;
}
</style>