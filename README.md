
```markdown
# Comprehensive Nexus API Documentation

This repository contains comprehensive documentation of the Nexus API. The documentation is organized into the following sections:

- [Introduction](#introduction)
- [Repositories](#repositories)
- [Artifacts](#artifacts)
- [Components](#components)
- [Blob Stores](#blob-stores)
- [Tasks](#tasks)
- [Health Check](#health-check)
- [Security](#security)
- [Proxies](#proxies)

## Introduction

The Nexus API is a RESTful API that allows you to interact with the Nexus Repository Manager. The API provides endpoints to manage repositories, artifacts, components, blob stores, tasks, health check, security, and proxies. The API is documented in the Nexus Repository Manager documentation.

## Repositories

The repositories endpoint allows you to manage repositories in the Nexus Repository Manager. You can create, read, update, and delete repositories using the API.

### List Repositories

```sh
curl -u username:password -X GET "http://<nexus-url>/service/rest/v1/repositories"
```

### Get Details of a Specific Repository

```sh
curl -u username:password -X GET "http://<nexus-url>/service/rest/v1/repositories/<repository-name>"
```

### Create a New Repository (e.g., Maven Hosted)

```sh
curl -u username:password -X POST "http://<nexus-url>/service/rest/v1/repositories/maven/hosted" -H "Content-Type: application/json" -d '{
  "name": "maven-releases",
  "online": true,
  "storage": {
    "blobStoreName": "default",
    "strictContentTypeValidation": true
  },
  "cleanup": {
    "policyNames": [
      "string"
    ]
  },
  "maven": {
    "versionPolicy": "RELEASE",
    "layoutPolicy": "STRICT"
  }
}'
```

### Delete Repository

```sh
curl -u username:password -X DELETE "http://<nexus-url>/service/rest/v1/repositories/<repository-name>"
```

## Artifacts

### Upload an Artifact

```sh
curl -u username:password -X POST "http://<nexus-url>/repository/<repository-name>/com/example/my-artifact/1.0.0/my-artifact-1.0.0.jar" --upload-file /path/to/my-artifact-1.0.0.jar
```

### Search for Artifacts

```sh
curl -u username:password -X GET "http://<nexus-url>/service/rest/v1/search/assets?repository=<repository-name>&group=com.example&name=my-artifact&version=1.0.0"
```

### Delete Artifact

```sh
curl -u username:password -X DELETE "http://<nexus-url>/repository/<repository-name>/com/example/my-artifact/1.0.0/my-artifact-1.0.0.jar"
```

## Components

### List Components in a Repository

```sh
curl -u username:password -X GET "http://<nexus-url>/service/rest/v1/components?repository=<repository-name>"
```

### Get Details of a Component

```sh
curl -u username:password -X GET "http://<nexus-url>/service/rest/v1/components/<component-id>"
```

### Delete a Component

```sh
curl -u username:password -X DELETE "http://<nexus-url>/service/rest/v1/components/<component-id>"
```

## Blob Stores

### List Blob Stores

```sh
curl -u username:password -X GET "http://<nexus-url>/service/rest/v1/blobstores"
```

### Create a Blob Store

```sh
curl -u username:password -X POST "http://<nexus-url>/service/rest/v1/blobstores" -H "Content-Type: application/json" -d '{
  "name": "blobstore-name",
  "type": "FileBlobStore",
  "attributes": {
    "path": "/path/to/blobstore"
  }
}'
```

### Delete a Blob Store

```sh
curl -u username:password -X DELETE "http://<nexus-url>/service/rest/v1/blobstores/<blobstore-name>"
```

## Tasks

### List Tasks

```sh
curl -u username:password -X GET "http://<nexus-url>/service/rest/v1/tasks"
```

### Run a Task

```sh
curl -u username:password -X POST "http://<nexus-url>/service/rest/v1/tasks/<task-id>/run"
```

## Health Check

### Check Health

```sh
curl -u username:password -X GET "http://<nexus-url>/service/rest/v1/healthcheck"
```

### Check System Information

```sh
curl -u username:password -X GET "http://<nexus-url>/service/rest/v1/system/info"
```

## Security

### List Users

```sh
curl -u username:password -X GET "http://<nexus-url>/service/rest/v1/security/users"
```

### Create a User

```sh
curl -u username:password -X POST -H "Content-Type: application/json" -d '{
  "userId": "new-user",
  "firstName": "New",
  "lastName": "User",
  "email": "new.user@example.com",
  "password": "password",
  "roles": ["nx-admin"]
}' "http://<nexus-url>/service/rest/v1/security/users"
```

### Delete a User

```sh
curl -u username:password -X DELETE "http://<nexus-url>/service/rest/v1/security/users/<user-id>"
```

## Proxies

### List Proxies

```sh
curl -u username:password -X GET "http://<nexus-url>/service/rest/v1/proxy"
```

### Create a Proxy

```sh
curl -u username:password -X POST -H "Content-Type: application/json" -d '{
  "name": "my-proxy",
  "type": "proxy",
  "format": "maven2",
  "online": true,
  "storage": {
    "blobStoreName": "default",
    "strictContentTypeValidation": true
  },
  "proxy": {
    "remoteUrl": "https://repo1.maven.org/maven2/",
    "contentMaxAge": 1440,
    "metadataMaxAge": 1440
  }
}' "http://<nexus-url>/service/rest/v1/proxy"
```

## Notes

- Replace `<nexus-url>` with the URL of your Nexus Repository Manager.
- Replace `<repository-name>` with the name of the repository.
- Replace `<component-id>` with the ID of the component.
- Replace `<blobstore-name>` with the name of the blob store.
- Replace `<task-id>` with the ID of the task.
- Replace `<user-id>` with the ID of the user.
- Replace `username:password` with your Nexus Repository Manager credentials.
- Replace `/path/to/my-artifact-1.0.0.jar` with the path to the artifact file.
- Replace `groupId`, `artifactId`, and `version` in the artifact URLs with the appropriate values.
- The examples provided in this documentation are for illustration purposes only. Please refer to the Nexus Repository Manager documentation for detailed information on the API endpoints and parameters.
```