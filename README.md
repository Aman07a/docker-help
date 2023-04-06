# Docker Settings

To make your Docker image publicly accessible or grant access to specific users, you can use the Docker Hub repository settings.

1. Log in to Docker Hub and navigate to the repository page that you want to share.
2. Click on the "Settings" tab at the top of the page.
3. Under the "Visibility" section, select "Public" if you want to make the Docker image publicly accessible, or "Private" if you want to grant access to specific users.
4. If you selected "Private", you can grant access to specific users by entering their Docker Hub usernames or email addresses in the "Access Settings" section.
5. Click the "Save Changes" button to update the repository settings.
If you made your Docker image publicly accessible, anyone can pull the image using the `docker pull` command with the repository name, like `docker pull aman07a/myapp`.

If you granted access to specific users, they will need to log in to Docker Hub using the `docker login` command with their own Docker Hub credentials before they can pull the image.

Note that you can also control access to your Docker images using organization memberships or teams on Docker Hub. This can be useful for managing access to images within a larger group or organization.

## Build:
```bash
docker build -t aman07a/hello-world-python:0.0.2.RELEASE .
```
```bash
docker build -t aman07a/hello-world-nodejs:0.0.2.RELEASE .
```
```bash
docker build -t aman07a/hello-world-java:0.0.2.RELEASE .
```
```bash
docker build -t aman07a/currency-exchange:0.0.1-RELEASE .
```
```bash
docker build -t aman07a/currency-conversion:0.0.1-RELEASE .
```

## Run:
```bash
docker run -p 5000:5000 aman07a/hello-world-python:0.0.2.RELEASE
```
```bash
docker run -p 5000:5000 aman07a/hello-world-nodejs:0.0.2.RELEASE
```
```bash
docker run -p 5000:5000 aman07a/hello-world-java:0.0.2.RELEASE
```
```bash
docker run -p 8000:8000 --name=currency-exchange aman07a/currency-exchange:0.0.1-RELEASE
```
```bash
docker run -p 8100:8100 --name=currency-conversion aman07a/currency-conversion:0.0.1-RELEASE
```

## Run (detached):
```bash
docker run -p 5000:5000 -d aman07a/hello-world-python:0.0.2.RELEASE
```
```bash
docker run -p 5000:5000 -d aman07a/hello-world-nodejs:0.0.2.RELEASE
```
```bash
docker run -p 5000:5000 -d aman07a/hello-world-java:0.0.2.RELEASE
```
```bash
docker run -p 8000:8000 -d --name=currency-exchange aman07a/currency-exchange:0.0.1-RELEASE
```
```bash
docker run -p 8100:8100 -d --name=currency-conversion aman07a/currency-conversion:0.0.1-RELEASE
```

## Push (Publishing to the Docker Hub):
```bash
docker push aman07a/hello-world-python:0.0.2.RELEASE
```
```bash
docker push aman07a/hello-world-nodejs:0.0.2.RELEASE
```
```bash
docker push aman07a/hello-world-java:0.0.2.RELEASE
```

## Response (currency):
```url
http://localhost:8000/currency-exchange/from/EUR/to/INR
```
```url
http://localhost:8100/currency-conversion/from/EUR/to/INR/quantity/10
```

## Containers
### List of containers:
```bash
docker container ls
```

### Stop active container:
```bash
docker container stop currency-conversion
```

### Remove container:
```bash
docker container rm currency-conversion
```

## Networking:
### Create new network:
```bash
docker network create currency-network
```

## Linking containers:
- You don't want to HARDCODE
- Configure an Environment Variable - `CURRENCY_EXCHANGE_SERVICE_HOST`
- --env CURRENCY_EXCHANGE_SERVICE_HOST=http://currency-exchange
```url
docker run -p 8100:8100 -d --env CURRENCY_EXCHANGE_SERVICE_HOST=http://currency-exchange --name=currency-conversion --link currency-exchange in28min/currency-conversion:0.0.1-RELEASE
```

## Logs:
```bash
docker logs currency-conversion
```
```bash
docker logs -f 123456789
```

## Images:
### List of images:
```bash
docker images
```

## Authentication:
### Docker image pushing to Docker Hub:
To push the Docker image to a container registry like Docker Hub under the username `aman07a`, follow these steps:

Log in to Docker Hub from the command line using the docker login command:
```bash
docker login --username=aman07a
```
You will be prompted to enter your Docker Hub password.

Tag the Docker image with the Docker Hub repository name:
```bash
docker tag myapp aman07a/myapp
```
Here, `myapp` is the name of the local Docker image, and aman07a is your Docker Hub username.

Push the Docker image to Docker Hub using the docker push command:
```bash
docker push aman07a/myapp
```
This will upload the Docker image to your Docker Hub account.

Note that you can also specify a version tag for the Docker image by appending a colon and a version tag to the image name, like `aman07a/myapp:1.0`. This can be useful for versioning your Docker images.

Also, keep in mind that you may need to make the Docker image publicly accessible or grant access to specific users if you want to share it with others.
