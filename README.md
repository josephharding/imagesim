
## ImageSim

Given a directory of JPEG images, calculate how similar each image is to every other image.

NOTE: This code is a modified version of Google's TensorFlow tutorial on the Inception model to show similarity between images, my contribution is primarily in dockerizing for ease of use.

### Prereqs

1. Docker (tested with version 2.0.0.0-mac81 (29211), Docker Engine 18.09.0)

### Build

First, build the two docker images, `imagesim-vectorize` and `imagesim-cluster`:

```
./build
```

This will take a few minutes as an Ubuntu base environment is setup with support for CUDA enabled Tensorflow libraries.

### Run

To get started, try using these images: https://drive.google.com/file/d/1THdx5I-JIKvCx6c_DDh82_U1l5KJYS19/view?usp=sharing, and unzip them into `/tmp/imagesim_images`

Now, generate image similarity values for these with the run command:

```
./run
```

Using the images linked above, your expected output should look like this:

```
imagesim (master) $ ls /tmp/imagesim_out/
cabin0.json  cabin1.json  cabin2.json  cabin3.json  modern0.json  modern1.json  modern2.json  modern3.json
imagesim (master) $ cat /tmp/imagesim_out/cabin0.json
[{"similarity": 1.0, "filename": "cabin0"}, {"similarity": 0.791, "filename": "cabin2"}, {"similarity": 0.756, "filename": "cabin3"}, {"similarity": 0.7449, "filename": "cabin1"}, {"similarity": 0.6627, "filename": "modern0"}, {"similarity": 0.6289, "filename": "modern3"}, {"similarity": 0.5995, "filename": "modern2"}, {"similarity": 0.5952, "filename": "modern1"}]
```

Now try adding a new JPEG to the images directory and see how similar it is to the existing images!

### Customization of Paths

If you don't want to use the default paths in `/tmp`, edit the `IMAGE_DIR`, `VECTOR_DIR`, `OUT_DIR` variables in the file `run` to change where the script should find your images, where to place the vector representation of each image (this is useful if you'd like to inspect the raw vector for debugging), and where to place the final output json that contains the similarity value of each image to every other image.

NOTE: These variables are used as docker volumes, which do not support relative paths, so please make sure to use absolute paths: https://github.com/moby/moby/issues/4830
