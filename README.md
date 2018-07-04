# Project: Search and Sample Return 

[//]: # (Image References)

[grid_image]: ./calibration_images/example_grid1.jpg
[perspective_transformed]: ./output/perspective_transformed.png
[threshed_birds_view]: ./output/threshed_birds_view.png
[mean_direction]: ./output/mean_direction.png
[rock]: ./output/rock.png
[image2]: ./calibration_images/example_grid1.jpg
[image3]: ./calibration_images/example_rock1.jpg

## [Rubric](https://review.udacity.com/#!/rubrics/916/view) Points

Here I will consider the rubric points individually and describe how I addressed each point in my implementation.  

### Notebook Analysis

#### Image processing steps

1. First use perspective transfrom to transform image from camera view to birds view.

    ![alt text][grid_image]
    ![alt text][perspective_transformed]

2. Transform the bird view image to black and white using color thresh.

    ![alt text][threshed_birds_view]

3. Get the mean direction of all white pixels.

    ![alt text][mean_direction]

4. Extract rock from image using color threshing

    ![alt text][rock]

#### Image processing result

See `./output/test_mapping.mp4`.

### Autonomous Navigation and Mapping

#### `perception_step()`

`perceptions_step()` follow the same step of `process_image()` on the IPython notebook on reachable part, obstacles and pickable rock:

1. Transform the image from camera view to bird's view.

2. Using color threshing to extract inserested parts/pixels from bird's view images.

3. Transform pixels obtained from last steps to world map coordiates and draw on the world map.

4. Get the distance and angles on rover center coordinate to naviagte the rover.

#### `decision_step()`

#### 2. Launching in autonomous mode your rover can navigate and map autonomously.  Explain your results and how you might improve them in your writeup.  

**Note: running the simulator with different choices of resolution and graphics quality may produce different results, particularly on different machines!  Make a note of your simulator settings (resolution and graphics quality set on launch) and frames per second (FPS output to terminal by `drive_rover.py`) in your writeup when you submit the project so your reviewer can reproduce your results.**

The rover will stuck on a rock that part of the rock aren't on the gourd. In this condition, the rover think the rock is passable but actually been blocked by in the middle part of the rock.
