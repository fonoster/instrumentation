# Instrumentation Service

> Takes an instrumentation key and returns creates new resources

![publish to docker](https://github.com/fonoster/fonos-nodejsmc/workflows/publish%20to%20docker%20hub/badge.svg)

This service takes a request with an intrumentation key, typically from a webclient, and creates a set of resources such as a SIP User Agent, Domains, etc. 

## Available Versions

You can see all images available to pull from Docker Hub via the [Tags](https://hub.docker.com/repository/registry-1.docker.io/fonoster/instrumentation/tags?page=1) page. Docker tag names that begin with a "change type" word such as task, bug, or feature are available for testing and may be removed at any time.

## Installation

You can clone this repository and manually build it.

```
cd fonos-nodejsmc
docker build -t fonoster/instrumentation:%%VERSION%% .
```

Otherwise you can pull this image from docker index.

```
docker pull fonoster/instrumentation:latest:%%VERSION%%
```

## Usage Example

The following is a minimal example of using this image.

```bash
docker run -it \
    -v /path/to/config:/home/fonos/.fonos/config
    -v /path/to/instrumentation.json:/home/fonos/.fonos/instrumentation.json
    -p 4573:4573 \
    fonoster/instrumentation
```

## Environment Variables

Run environment variables are used in the entry point script to render configuration templates. You can specify the values of these variables during `docker run`, `docker-compose up`, or in Kubernetes manifests in the `env` array.

- `CONFIG` - Contains the credentials and endpoint information to connect with an Fonos API Server.

## Exposed ports

- `3000` - Default http port for restful API

## Volumes

- `/home/fonos/.fonos/config` - Fonos connection config.
- `/home/fonos/.fonos/instrumentation.json` - File with instrumentation info, such as productId, accessKeyId, etc.

## Contributing

Please read [CONTRIBUTING.md](https://github.com/fonoster/fonos/blob/master/CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

## Authors

- [Pedro Sanders](https://github.com/psanders)

See also the list of contributors who [participated](https://github.com/fonoster/instrumentation/contributors) in this project.

## License

Copyright (C) 2020 by Fonoster Inc. MIT License (see [LICENSE](https://github.com/fonoster/fonos/blob/master/LICENSE) for details).
