Verify that you can push to host.docker.internal:5000/myregistry/<image_name>

-pull an image to push 

`$ docker pull ubuntu`

-tag the shell with with local port (the extra tag ":latest" is specifically for the ubuntu image)

`$ docker tag ubuntu:latest host.docker.internal:5000/myregistry`

-Finally push the ubuntu image to your repository

`$ docker push host.docker.internal:5000/myregistry`

