# About

This project was created to test the Docker Mult Platform Build.

The application is very simple, only to run and test if it is working.

Use the docker buildx to build the application with mult-platform way.

[Doc](https://docs.docker.com/build/building/multi-platform/)

# Want to test the application?

Run the application

```bash
npm install
npm start
```

Test the application

```bash
curl localhost:3000/
```

# Configure the docker buildx

Configure the buildx builder

```bash
docker buildx create --name mybuilder
docker buildx use mybuilder
```

Verify the builder

```bash
docker buildx inspect --bootstrap
```

# Login on the docker registry

Login on your docker registry.

ex for docker hub:

```bash
docker login
```

# Build the app

Execute the build with the argument: -t YOURREGISTRY/APPNAME:TAG

ex:

```bash
docker buildx build --platform linux/amd64,linux/arm64 -t gustavoapolinario/mult-platform-container:latest --push .
```

# Verify the image builded

The command below will show informations about the image.

```bash
docker buildx imagetools inspect gustavoapolinario/mult-platform-container:latest
```

To be simple, let's get only the Platform from result:

```bash
docker buildx imagetools inspect gustavoapolinario/mult-platform-container:latest | grep Platform
```
The result:

```text
  Platform:    linux/amd64
  Platform:    linux/arm64
```

You can see in docker hub the OS/ARCH supported by the image.

Go to your docker hub repository, select your app, click on the tag. The link will send you to a page with a combobox showing the image supported OS/ARCH.
