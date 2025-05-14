---
title: "Blender_GN_Experiment"
layout: portfolio
classes: wide
published: true
excerpt: "Experiment with geomtry node for point cloud simulations. Finding ways to visually communicate design in early prototyping phase."
header:
  # video:
  #   id: hvH1B8AQMQg
  #   provider: youtube
  image: https://dl.dropbox.com/scl/fi/5z8mvyndll6kuy59bakwt/banner_01.png?rlkey=7ggva35166ko43byykmh27lxw&dl=0
  teaser: https://dl.dropbox.com/scl/fi/wxqog5pyamr3wqimyx1co/Comp-2.gif?rlkey=nvipc017ihgp0wnqvgnwm8vsj&dl=0
sidebar:
  - title: "Role"
    image: assets/images/blender_logo_kit/square/blender_icon_256x256.png
    image_alt: "logo"
    text: "Trainer"
  - title: "Responsibilities"
    text: "3D asset generation using Stucture from motion(SfM) technique, create a point cloud data set and reanimate for presentation and fun purpose"
gallery:
  - url: https://dl.dropbox.com/scl/fi/dyf0m1jsui010zpjqzxbc/blender_iTS0K7nu2D.png?rlkey=hmagefy1mpq9rzihu3n9ujq2p&dl=0
    image_path: https://dl.dropbox.com/scl/fi/dyf0m1jsui010zpjqzxbc/blender_iTS0K7nu2D.png?rlkey=hmagefy1mpq9rzihu3n9ujq2p&dl=0
    alt: "image_01"
  - url: https://dl.dropbox.com/scl/fi/o9exuk9dwg2b8xgnawec8/blender_sPfJQ6iZWO.jpg?rlkey=y84i5zyy3ed9bxfmstzud1d77&dl=0
    image_path: https://dl.dropbox.com/scl/fi/o9exuk9dwg2b8xgnawec8/blender_sPfJQ6iZWO.jpg?rlkey=y84i5zyy3ed9bxfmstzud1d77&dl=0
    alt: "image_02"
gallery2:
  - url: https://dl.dropbox.com/scl/fi/p4m24wri7ksfu2hwtgm3z/blender_32oH0IhflA.png?rlkey=43b57ap0nm37fodliz0ymzwxu&dl=0
    image_path: https://dl.dropbox.com/scl/fi/p4m24wri7ksfu2hwtgm3z/blender_32oH0IhflA.png?rlkey=43b57ap0nm37fodliz0ymzwxu&dl=0
    alt: "image_01"
  - url: https://dl.dropbox.com/scl/fi/78ot22ou3r9tfo72blvp9/blender_lJJrFlvn3n.png?rlkey=q9mqgua1bxraxvtts1nlmoev3&dl=0
    image_path: https://dl.dropbox.com/scl/fi/78ot22ou3r9tfo72blvp9/blender_lJJrFlvn3n.png?rlkey=q9mqgua1bxraxvtts1nlmoev3&dl=0
    alt: "image_02"

---

The Geometry Nodes feature in Blender is relatively new but is incredibly powerful. This node-based system allows users to create complex 3D models and effects without the need for coding. I often find myself amazed by how much this tool offers compared to higher-end solutions like Houdini. As a result, I decided to experiment with it and conduct a few small projects.

<h2>Point Cloud Object</h2>

<iframe width="560" height="315" src="https://www.youtube.com/embed/lI6tBXr61C0?si=COlLQeTGmWXkDdvK" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

My first experiment involved creating a procedural point cloud system that dynamically distributes and modifies points on a mesh's surface. It begins by randomly distributing points across the faces of the input geometry, which is controlled by a Density parameter. This allows me to adjust how densely the points are placed. These points serve as the foundation for further procedural modifications.

To alter the positions of the points, I used a Noise Texture combined with their original positions. The noise introduces random variations, creating organic-looking displacements. A Color Ramp remaps the noise intensity, giving users precise control over how the displacement affects the points. Only specific axes, such as the Z-axis, are influenced, ensuring a controlled and visually appealing offset.

Each point is assigned a random radius, adding variability to their size. This randomness is fine-tuned with mathematical operations to keep the point sizes within a specified range. The points are then assigned a material for styling, making them ready for rendering. The final output is a fully customizable, noise-driven point cloud, which can be used for effects like debris simulation, abstract art, or particle-based visualizations.

{% include gallery caption="Point Cloud using Polycam + Blender Geometry Nodes." %}

<h2>Lidar Point Cloud Simulation</h2>

<iframe width="560" height="315" src="https://www.youtube.com/embed/q7KAyYGVOu0?si=ytEtATD0tgFvVTPS" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

In another setup, I created a system that simulates a LiDAR-like point sampling mechanism by projecting and instancing points onto a target object. This system is particularly useful for tasks like surface sampling, procedural asset placement, or simulating point-cloud projections, frequently used in autonomous vehicle sensors. It begins by generating a UV Sphere, defined by parameters for segments, rings, and radius. The geometry is then filtered using a condition that removes certain points, such as those with specific Z-axis positions, leaving only the desired geometry for further processing.

Next, the remaining points on the sphere are modified based on their positions and normals to prepare them for alignment with another object. The geometry is converted into points, which are then processed using the Raycast node. This node projects rays from the points toward a target object, capturing the hit positions where the rays intersect. These hit positions are used to align the points or geometry accurately onto the surface of the target.

Finally, small spheres are instanced at these sampled points to visualize the LiDAR-like scanning effect. A material is applied to the instanced geometry for styling, and the final result is passed to the Group Output. I experimented with this setup to simulate point-cloud projections, surface sampling, or procedural asset placement workflows commonly used in autonomous vehicle sensors.

{% include gallery id="gallery2" caption="Simulate Lidar sensory effect using Blender Geometry Nodes." %}

Looking towards the future, I envision AI-enabled integration, real-time procedural generation, and improved performance. While Blender's Geometry Nodes is a powerful tool, its single-threaded nature still limits its capabilities.Houdini's multi cores and threads feature. Additionally, Houdini also has better optimized execution and memory management, make it a better suited solution to handle large complex scene.  
