
## ImageSim

Given a directory of JPEG images, calculate the distance of each image from every other image.

Code is modified version of Google's TensorFlow tutorial on the Inception model to show distances between images.

### Prereqs

1. Docker

### Build

Build the two docker images, `imagesim-vectorize` and `imagesim-cluster`:

```
./build
```

### Run

Edit the `IMAGE_DIR`, `VECTOR_DIR`, `OUT_DIR` variables to change where the script should find your images, where to place the vector representation of each image (this is useful if you'd like to inspect the raw vector for debugging), and where to place the final output json values that contain the distance to each other image per image.

NOTE: These variables are used as docker volumes, which do not support relative paths, so please make sure to use absolute paths: https://github.com/moby/moby/issues/4830

Once you've specified an absolute path to a directory with JPEG images inside it, you can generate image similarity values for these with the run command:

```
./run
```
