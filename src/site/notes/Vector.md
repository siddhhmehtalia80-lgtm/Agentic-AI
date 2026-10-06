---
{"dg-publish":true,"permalink":"/vector/","dg-note-properties":{}}
---

see:[[LLMs\|LLMs]]
Depending on the context—math, physics, or artificial intelligence—a **vector** has slightly different meanings, but the core concept is always about **representing magnitude, direction, or characteristics in a structured format**.

### 1. Vector in Physics and Mathematics

In math and physics, a vector is a quantity that has both **magnitude (size)** and **direction**.

- **Scalar vs. Vector:**
    
    - A **scalar** is just a single number (e.g., speed: _60 mph_, temperature: _72°F_).
        
    - A **vector** includes direction (e.g., velocity: _60 mph North_).
        
- **Representation:** It is visually drawn as an arrow. The length of the arrow represents the magnitude, and the arrowhead points in the direction.
    
- **Algebraically:** A vector is written as an ordered array of numbers, representing coordinates in space:
    
    $$\vec{v} = (x, y, z)$$
    
    - In 2D space: $(3, 4)$ means moving 3 units along the X-axis and 4 units along the Y-axis.
        
    - In 3D space: $(3, 4, 5)$ adds depth along the Z-axis.
        

### 2. Vector in Computer Science and Artificial Intelligence

In AI and Data Science, a vector is an **array (list) of numbers** that represents complex data—such as words, sentences, images, or audio—in a mathematical space. These are called **Vector Embeddings**.

#### How Vector Embeddings Work in AI:

Computers cannot directly understand human language or visual concepts; they only process numbers. Embedding models convert unstructured data into numerical vectors.

1. **Dimensionality (Features):**
    
    Instead of 2 or 3 dimensions, an AI vector might have **768 to 1536+ dimensions**. Each dimension represents an abstract feature or relationship learned by a neural network model.
    
2. **Spatial Similarity (Semantic Mapping):**
    
    The key principle is that **items with similar meanings are placed close to each other in vector space**.
    
    - _Example:_ The vector for "Dog" will be geometrically very close to "Puppy" or "Canine", but far away from "Airplane".
        
3. **Mathematical Relationships:**
    
    Because data is converted into geometry, mathematical operations work on concepts.
    
    $$\text{"King"} - \text{"Man"} + \text{"Woman"} \approx \text{"Queen"}$$
    

#### Measuring Similarity:

To compare two vectors (e.g., matching a search query to a database document), algorithms measure distance or angles between vectors in multi-dimensional space:

- **Cosine Similarity:** Measures the angle between two vectors (whether they point in the same direction).
    
- **Euclidean Distance:** Measures the straight-line distance between two points in vector space.
    

### 3. Vector in Computer Graphics (Vector Graphics)

In design and graphics (e.g., SVG files, Adobe Illustrator), a **vector graphic** uses mathematical formulas to draw points, lines, curves, and shapes rather than a grid of colored pixels (bitmaps like JPEGs or PNGs).

- **How it works:** Instead of saving a pixel grid, a vector file saves instructions like _"draw a circle with radius 10 at coordinate (50,50)"_.
    
- **Benefit:** You can scale vector images infinitely without losing quality or becoming pixelated.
    

### Summary Comparison

| **Field**                   | **What a Vector is**                          | **Primary Purpose**                                           |
| --------------------------- | --------------------------------------------- | ------------------------------------------------------------- |
| **Math / Physics**          | Quantity with magnitude & direction           | Describing physical movement, forces, and spatial positions.  |
| **Artificial Intelligence** | Array of numbers representing data features   | Enabling AI to calculate meaning, context, and similarity.    |
| **Graphics**                | Shapes defined by mathematical control points | Creating scalable logos and graphics that don't lose quality. |