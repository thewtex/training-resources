---
title: Watershed
layout: module
tags: ["draft"]
prerequisites:
  - "[Connected-component analysis](../connected_components)"
  - "[Distance transform](../distance_transform)"
objectives:
  - "Understand the concept of watersheds in image analysis."
  - "Understand that a watershed algorithm is often applied to a distance map to split objects by their shape."
  - "Be able to run a watershed algorithm in an image analysis platform."
motivation: |
  The segmentation of touching objects often is a challenge in image analysis. The watershed algorithm is a very common operation to split touching objects and is available in most image analysis frameworks.

concept_map: >
  graph TD
    T("Image") --> W("Watershed algorithm")
    W --> S("Segmented image")
    S --- B("Boundaries/Watersheds: Intensity ridges")
    S --- R("Regions/Basins")


figure: /figures/watershed.png
figure_legend: Illustration of the watershed transform. a) Image with three objects that cannot be separated by a simple threshold. b) Foreground background segmentation of (a). c) Watershed transform of (e). d) (c) masked with (d). e) Inverse of (a). f) Intensity line profile along the line depicted in (e) with illustration of filling up the basins up to a the level where the yellow and blue regions meet and a watershed is build. g) as (f) but filling up the basins to a higher level.

activity_preface: |
  - Basic watershed
    - Open [xy_8bit__touching_objects.tif](https://github.com/NEUBIAS/training-resources/raw/master/image_data/xy_8bit__touching_objects.tif).
    - Appreciate that you cannot segment the three objects using a simple threshold.
    - Anyway find a threshold that segments the image into foreground (objects) and background
      - Keep this binary mask, we will need it later.
    - Invert the original image and apply the watershed transform.
    - Appreciate that the image is now split into three regions.
    - Combine the binary mask and the watershed image to segment the three objects.
  - Shape watershed
     - Open [xy_8bit__touching_objects_same_intensity.tif](https://github.com/NEUBIAS/training-resources/raw/master/image_data/xy_8bit__touching_objects_same_intensity.tif).
    - Appreciate that you cannot segment the three objects using a simple threshold.
    - Appreciate that also a watershed algorithm does not help here, because there is no "intensity ridge" bewteen the two touching objects.
    - Create a binary mask
    - Create a distance map within objects
    - Invert the distance map
    - Slightly blur the distance map to avoid spurious minima (water basins)
    - Apply a watershed transform
    - Combine the binary mask and the watershed image to segment the two objects

activities:
- ["ImageJ Macro: MorpholibJ basic watershed", "watershed/activities/morpholibj_basic_watershed.ijm", "java"]
- ["ImageJ Macro: MorpholibJ shape watershed", "watershed/activities/morpholibj_shape_watershed.ijm", "java"]

exercise_preface: |
  - Open [xy_8bit__few_separate_nuclei.tif](https://github.com/NEUBIAS/training-resources/raw/master/image_data/xy_8bit__few_separate_nuclei.tif)
  - There are 6 (partially visible) nuclei.
  - Apply the watershed algorithm to segment the image into 6 regions.
  - Hint: You will need to preprocess (invert and smooth) the image.

exercises:
  - ["ImageJ Macro: MorpholibJ: ???", "watershed/exercises/morpholibj_watershed_noise.md"]

assessment: >

  ### Fill in the blanks

    1. TODO ___ .
    1. TODO ___ .
    
    > ## Solution
    >   1. TODO
    >   1. TODO
    {: .solution}

learn_next:

external_links:
  - "[Wikipedia: Watershed image processing](https://en.wikipedia.org/wiki/Watershed_(image_processing))"
---
