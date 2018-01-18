# giespaepen - dockerfiles

> I needed some specific Docker containers to build my code in various CI environments. You can find the dockerfiles in this project in order to create an automated build in DockerHub.

## Build a container
In each dir `<dir>` run the following build command:

```bash
docker build . -t <reponame>/<dir>:latest
```

Publish the docker images by:

```bash
docker push <reponame>/<dir>:latest
```

## node-yarn

Simple build container to build an NodeJS project with yarn. The following versions are installed:

- **NodeJS**: 7+
- **NPM**: 4+
- **Yarn**: latest

The main purpose of this build container is to use it in your CI environment. Pull the container and run your code in it like so:

```bash
docker run -i --name <an image name> -v `pwd`:/build giespaepen/node-yarn:latest
```

The following actions are run on entry in the `/build` folder:

- `yarn install`
- `yarn build`
- `yarn test`

## hugo-builder

Simple build container to build a hugo site. The main purpose of this build container is to use it in your CI environment. Pull the container and run your code in it like so:

```bash
docker run -i --name <an image name> -v `pwd`:/build giespaepen/hugo-builder:latest
```

The following actions are run on entry in the `/build` folder:

- `hugo`

## centos7-yarn

Simple build container to build an NodeJS project with yarn. The following versions are installed:

- **NodeJS**: 6.10 (LTS)
- **NPM**: 3+
- **Yarn**: latest

The main purpose of this build container is to use it in your CI environment and also build binary dependencies targetting Centos7/RHEL. Pull the container and run your code in it like so:

```bash
docker run -i --name <an image name> -v `pwd`:/build giespaepen/centos7-node:latest
```

The following actions are run on entry in the `/build` folder:

- `yarn install`
- `npm rebuild`
- `yarn build`
- `npm test`
