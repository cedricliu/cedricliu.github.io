---
layout: single
classes: wide
title: Drawing Lines in Unity
date: 2023-08-17 09:29:59 -0700
categories: ComputerGraphics 
---

As a technical artist working with game programming and computer graphics, I often find myself relying on the tools readily available to me, without delving into the underlying mathematics. Recently, I revisited the book "Mathematics for Game Programming and Computer Graphics" by Penny De Byl, and it sparked a curiosity to understand the bigger picture behind these tools.

This exploration led me to a study comparing how lines are drawn using a pixel-based solution versus the methods commonly used in Unity. These notes not only serve as a personal learning journey but also provide insights that may be valuable to other developers and artists looking to deepen their understanding of line drawing techniques.

In this post, we'll dissect Bresenham's line algorithm, a classic approach to drawing lines on a pixel grid, and contrast it with Unity's built-in line rendering and vector graphics libraries. Whether you're a seasoned professional or a curious beginner, I hope this comparison sheds light on the intricate world of line rendering in Unity.

# Drawing Lines in Unity: Bresenham's Algorithm vs Built-in Solutions
When it comes to drawing lines in Unity, developers have several options at their disposal. In this post, we'll explore the use of Bresenham's line algorithm, a classic computer graphics method, and compare it to Unity's built-in line rendering solutions and vector graphics libraries.

## Bresenham's Line Algorithm
Bresenham's line algorithm is a mathematical approach to drawing straight lines on a pixel grid. It's widely used in computer graphics and can be implemented in Unity by modifying individual pixels on a texture. Here's an example of how you can use this algorithm to draw a line on a `Texture2D`:

```csharp
// Example code for Bresenham's line algorithm in Unity
using UnityEngine;
using UnityEngine.UI;

public class DrawLine : MonoBehaviour
{
    public RawImage rawImage; // Assign the RawImage component here
    private Texture2D texture;

    private void Start()
    {
        texture = new Texture2D(512, 512);
        rawImage.texture = texture;

        // Draw a line from (50, 50) to (200, 300)
        BresenhamLine(50, 50, 200, 300, Color.red);

        // Apply changes
        texture.Apply();
    }

    private void BresenhamLine(int x1, int y1, int x2, int y2, Color color)
    {
        int dx = Mathf.Abs(x2 - x1);
        int dy = Mathf.Abs(y2 - y1);
        int sx = x1 < x2 ? 1 : -1;
        int sy = y1 < y2 ? 1 : -1;
        int err = (dx > dy ? dx : -dy) / 2;

        while (true)
        {
            SetPixel(x1, y1, color); // Set the pixel at (x1, y1)

            if (x1 == x2 && y1 == y2) break;

            int e2 = err;

            if (e2 > -dx) { err -= dy; x1 += sx; }
            if (e2 < dy) { err += dx; y1 += sy; }
        }
    }

    private void SetPixel(int x, int y, Color color)
    {
        if (x >= 0 && y >= 0 && x < texture.width && y < texture.height)
        {
            texture.SetPixel(x, y, color);
        }
    }
}

```

While this method provides full control over the pixels, it's worth considering how it compares to Unity's built-in solutions.

## Comparison with Unity's Built-in Line Rendering and Vector Graphics Libraries

### Bresenham's Algorithm (Using Texture2D)
- **Performance**: Potentially slow for large textures or frequent updates.
- **Flexibility**: Complete control over individual pixels.
- **3D Integration**: Requires additional work for 3D scenes.

### Unity's Built-in Line Renderer
- **Performance**: Optimized for real-time rendering in 3D space.
- **Flexibility**: Various styles, widths, and patterns.
- **3D Integration**: Easily integrated with 3D objects.

### Vector Graphics Libraries (e.g., SVG Importer)
- **Performance**: Generally optimized for both 2D and 3D rendering.
- **Flexibility**: Scalable and supports complex shapes.
- **3D Integration**: Some libraries support rendering in 3D space.

### Conclusion
- **Bresenham's Algorithm**: Use for pixel-level control or static images.
- **Line Renderer**: Use for 3D lines or paths requiring real-time performance.
- **Vector Graphics Libraries**: Use for complex 2D shapes or scalability.

Choosing the right approach to drawing lines in Unity depends on your specific needs and the complexity of your project. Bresenham's algorithm is suitable for pixel-level control, while Unity's built-in Line Renderer and vector graphics libraries provide higher-level abstractions optimized for performance.

Understanding these options empowers developers to make the right choice based on the requirements of their applications or games. Whether you're creating a 2D user interface or rendering complex 3D paths, Unity provides the flexibility to bring your vision to life.

--