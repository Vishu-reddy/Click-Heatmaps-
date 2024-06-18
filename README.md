<h1>Heatmap Visualization for Website User Interaction</h1>

<p>This project provides a Python script to visualize user interaction on a website using a heatmap overlayed on an image of the webpage. The script uses libraries such as Matplotlib, NumPy, and SciPy to create and display the heatmap.
Requirements</p>

<h3>Ensure you have the following Python libraries installed:</h3>
    <ul>
    <li>Matplotlib</li>
    <li>NumPy</li>
    <li>SciPy</li>
    </ul>
    <h4>pip commands :</h4>
    <p>pip install matplotlib numpy scipy
</p>
<h3>Usage</h3>

    <pre>Script Overview

    The provided script includes a function plot that generates a heatmap overlayed on an image of a webpage.</pre>
    <code>
    import matplotlib.pyplot as plt
    from matplotlib.colors import LinearSegmentedColormap
    import numpy as np
    import scipy.ndimage.filters as filters

    </code>
  <h3>Function Definition</h3>

    <p>The plot function creates the heatmap and saves it if a path is provided.</p>
    <code>
    def plot(data, title, image_path, save_path=None):
    colors = [(0, 0, 0, 0), (0, 1, 1), (0, 1, 0.75), (0, 1, 0), (0.75, 1, 0),
              (1, 1, 0), (1, 0.8, 0), (1, 0.7, 0), (1, 0, 0)]

    img = plt.imread(image_path)
    img = np.flipud(img)  # Flip the image vertically
    
    fig, ax = plt.subplots(figsize=(w/100, h/100))

    ax.imshow(img, extent=[0, w, 0, h])
    cm = LinearSegmentedColormap.from_list('sample', colors)

    plt.imshow(data, cmap=cm, alpha=0.5)
    plt.colorbar()
    plt.title(title)
    if save_path:
        plt.savefig(save_path)

    </code>
  <h3>Parameters</h3>
<pre>
    data: A NumPy array containing the interaction data.
    title: The title of the plot.
    image_path: Path to the background image of the webpage.
    save_path: (Optional) Path to save the generated plot.</pre>
    <code>
      w = 1869
h = 933
data = np.zeros(h * w)
data = data.reshape((h, w))

for x in range(780, 820):
    for y in range(430, 470):
        data[y][x] = 100

data = filters.gaussian_filter(data, sigma=15)

    </code>
  <h3>Plotting</h3>

  <pre>The script then calls the plot function to create and display the heatmap.</pre>
  <code>
  plot(data, 'Sample plot', "images/image.png", "C:/Users/saduv/shreya_project/output/output.png")

  </code>
  <h3>File Structure</h3>
<pre>
    images/image.png: Background image of the webpage.
    output/output.png: Path where the heatmap will be saved.</pre>
    <code>python heatmap_script.py
</code>
<p>This will generate a heatmap based on the sample data and save it to output/output.png.
</p>
<h3>License</h3>
<pre>
This project is licensed under the MIT License. See the LICENSE file for details.
Acknowledgements

    Matplotlib
    NumPy
    SciPy

This README provides a comprehensive guide to understand and run the script for generating a heatmap visualization of user interaction on a webpage.</pre>
