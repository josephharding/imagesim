

create vectors for all the images in a directory

```
docker run --runtime=nvidia -v /home/cecadmin/image_dir:/usr/src/app/image_dir -v /home/cecadmin/vectors:/usr/src/app/vectors --env-file=env-vectorize josephharding/imagesim-vectorize:e6914dd
```

calculate the nearest neighbors using the vectors calculated in the previous step

```
docker run -v /home/cecadmin/out:/usr/src/app/out -v /home/cecadmin/nearest_neighbors:/usr/src/app/nearest_neighbors -v /home/cecadmin/vectors:/usr/src/app/vectors --env-file=env-cluster josephharding/imagesim-cluster:945981f
```
