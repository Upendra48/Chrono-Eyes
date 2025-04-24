# Chrono-Eyes
An CNN-based model to classify the eyes into seasons.

## A. Defining the seasons for classification

 ### 1. Spring Season Eye Pattern
- **Eye Colors**: Light brown, green, hazel tones.
- **Key Features**:
  - **High Contrast**: Sharp contrast between the iris and sclera.
  - **Starburst/Sunburst Design**: Golden or white ring around the pupil.
  - **Flecks and Dots**: Orange or brown flecks within the iris.
  - **Halo Structure**: Circular halo surrounding the pupil.
- **Subtypes**:
  - **Warm Spring**: Halo and speckles, with rich warmth.
  - **Light Spring**: Halo with cloudiness, soft and luminous.
  - **Bright Spring**: Halo with spokes or streams, vibrant.

 ### 2. Autumn Season Eye Pattern
- **Eye Colors**: Amber, hazel, dark brown.
- **Key Features**:
  - **Swirling Borders**: Soft, erratic patterns surrounding the pupil.
  - **Freckles and Speckles**: Organic, petal-like formations in the iris.
  - **Sunburst Effect**: Sunburst pattern around the pupil.
  - **Opaque Appearance**: Opaque look for deeper-colored eyes.
- **Subtypes**:
  - **Dark Autumn**: Rich depth, spokes and speckles.
  - **Soft Autumn**: Muted with cloudiness and speckles.
  - **Warm Autumn**: Halo and speckles, warmth and radiance.

### 3. Winter Season Eye Pattern
- **Eye Colors**: Blue, gray, deep green, cool undertones.
- **Key Features**:
  - **Spokes and Lines**: Lines radiating from the pupil to the iris.
  - **Concentric Bands**: Circular bands around the iris.
  - **Radiating Fibers**: White, uniform fibers.
  - **Defined Border**: High contrast between iris and sclera.
- **Subtypes**:
  - **Cool Winter**: Cool undertones with spokes and cloudiness.
  - **Dark Winter**: Deep, dark eyes with spokes and speckles.
  - **Bright Winter**: High contrast, spokes, and a halo.

 ### 4. Summer Season Eye Pattern
- **Eye Colors**: Soft blues, grays, muted greens.
- **Key Features**:
  - **Cloudy Texture**: Smoky, ethereal look within the iris.
  - **Crackled Glass Texture**: Unique, complex texture in the iris.
  - **Flowering Structure**: Petals or crypts within the iris.
  - **Radiating Fibers**: Soft white fibers radiating from the pupil.
- **Subtypes**:
  - **Light Summer**: Halo and cloudiness, soft luminosity.
  - **Soft Summer**: Cloudiness and speckles, muted depth.
  - **Cool Summer**: Cool undertones with spokes and cloudiness.

## B. Features to Extract for Eye Pattern Classification

### 1. Eye Color
- **Description**: The color of the iris, which could be light brown, green, hazel, blue, gray, etc.
- **Method to Extract**: 
  - Use image processing techniques to segment the iris from the surrounding areas.
  - Apply color detection algorithms (e.g., k-means clustering) to identify dominant colors in the iris.

### 2. Contrast Between Iris and Sclera
- **Description**: The sharpness of the contrast between the iris (colored part of the eye) and the whites of the eye (sclera).
- **Method to Extract**: 
  - Use edge detection techniques like Canny edge detection or Sobel filters to find the boundary between the iris and sclera.
  - Compute the contrast based on pixel intensity difference between the iris and sclera regions.

### 3. Starburst/Sunburst Pattern
- **Description**: A radiating pattern around the pupil, often golden or white, resembling a star or sunburst.
- **Method to Extract**: 
  - Use pattern recognition methods like Hough Transform to detect radial lines or spokes originating from the pupil.
  - Detect concentric rings or radial designs in the iris region.

### 4. Flecks and Dots
- **Description**: Small, scattered spots within the iris that may be orange, brown, or other colors.
- **Method to Extract**: 
  - Use blob detection techniques (e.g., Laplacian of Gaussian) to identify circular flecks or dots.
  - Identify color patterns and texture variations within the iris.

### 5. Halo Structure
- **Description**: A circular doughnut-shaped structure around the pupil, contributing to the overall brightness of the eye.
- **Method to Extract**: 
  - Detect circular structures using Hough Circle Transform.
  - Identify bright regions near the pupil and measure their radius and intensity.

### 6. Swirling Borders
- **Description**: Soft, erratic patterns surrounding the iris, particularly in Autumn.
- **Method to Extract**: 
  - Use texture analysis methods to identify swirling patterns (e.g., Gabor filters or Local Binary Patterns).
  - Extract edge features around the iris to detect irregular, organic shapes.

### 7. Concentric Bands
- **Description**: Circular bands that encircle the iris, common in Winter eyes.
- **Method to Extract**: 
  - Use circular Hough transforms to detect concentric circular structures in the iris.
  - Analyze color transitions between concentric rings.

### 8. Radiating Fibers
- **Description**: Fibers that radiate from the pupil, creating a structured or luminous appearance.
- **Method to Extract**: 
  - Detect lines and structures extending radially from the pupil using techniques like Radon Transform.
  - Analyze fiber directionality and uniformity.

### 9. Crackled Glass Texture
- **Description**: A unique, crackled pattern found in Summer eyes.
- **Method to Extract**: 
  - Use texture analysis algorithms to detect crackled or fragmented patterns.
  - Apply fractal analysis to identify irregular, non-smooth regions in the iris.

### 10. Defined Borders
- **Description**: A sharp and defined border between the iris and sclera, common in Winter.
- **Method to Extract**: 
  - Detect edges around the iris using techniques like Sobel or Canny edge detection.
  - Measure the crispness or smoothness of the iris boundary.

### 11. Cloudy Texture
- **Description**: A smoky or cloud-like pattern within the iris, typical for Summer.
- **Method to Extract**: 
  - Use texture segmentation methods (e.g., Gabor wavelets) to extract cloudy or foggy patterns within the iris.
  - Detect regions with gradients and low contrast indicative of a cloudy look.

### 12. Speckles and Petals
- **Description**: Patterns that resemble speckles, dots, or petal-like formations within the iris.
- **Method to Extract**: 
  - Apply point pattern analysis or morphological operations to detect petal or dot-like patterns.
  - Use clustering techniques to identify scattered, localized regions of interest in the iris.

### 13. Edge Detection and Shape Analysis
- **Description**: Identifying the shape and edges of the iris and pupil.
- **Method to Extract**: 
  - Use edge detection (Canny/Sobel) to outline the iris and pupil.
  - Apply shape recognition techniques to analyze the geometry of the iris and pupil.

### 14. Texture Features
- **Description**: Texture features refer to the overall feel of the iris, whether it's smooth, cracked, swirling, or patterned.
- **Method to Extract**:
  - Use texture analysis algorithms such as Local Binary Patterns (LBP) or Gray-Level Co-occurrence Matrix (GLCM) to quantify the texture of the iris.

### 15. Pupil Size and Shape
- **Description**: The size and shape of the pupil may vary, influencing the overall appearance of the iris.
- **Method to Extract**: 
  - Use image segmentation to accurately identify and measure the pupil size and shape.

### Feature Summary Table

| Feature                   | Description                                            | Method to Extract                            |
|---------------------------|--------------------------------------------------------|----------------------------------------------|
| Eye Color                 | Iris color (e.g., brown, blue, hazel)                  | Color detection (e.g., K-means clustering)   |
| Contrast                  | Contrast between iris and sclera                       | Edge detection, contrast calculation         |
| Starburst/Sunburst        | Radiating pattern around the pupil                     | Hough Transform, pattern recognition        |
| Flecks and Dots           | Small spots in the iris                               | Blob detection, color/texture analysis       |
| Halo Structure            | Circular ring around the pupil                        | Hough Circle Transform, intensity analysis  |
| Swirling Borders          | Soft, erratic borders around the iris                 | Texture analysis (e.g., Gabor filters)      |
| Concentric Bands          | Circular bands around the iris                        | Hough Transform, color transition analysis   |
| Radiating Fibers          | Fibers radiating from the pupil                       | Radon Transform, line analysis               |
| Crackled Glass Texture    | Crackled pattern in the iris                          | Texture analysis, fractal analysis          |
| Defined Borders           | Clear boundary between iris and sclera                | Edge detection (Sobel/Canny)                 |
| Cloudy Texture            | Smoky, cloudy texture in the iris                     | Texture segmentation (e.g., Gabor wavelets)  |
| Speckles and Petals       | Small petal-like or speckled patterns                  | Point pattern analysis, morphological ops    |
| Edge Detection and Shape  | Shape of the iris and pupil                           | Shape recognition, edge detection           |
| Texture Features          | Overall texture of the iris                           | LBP, GLCM, texture analysis                 |
| Pupil Size and Shape      | Size and shape of the pupil                           | Image segmentation                          |






   
