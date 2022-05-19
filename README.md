# mirror_gcrio2docker_image
![github action](https://github.com/JaeGerW2016/mirror_gcrio2docker_image/actions/workflows/mirror_docker_image.yml/badge.svg)



Synchronize the `k8s.gcr.io` image from one registry to another through `github action`. For example, synchronize the specified docker image under `k8s.gcr.io` to `docker.io`.

## Usage

Open a new `issue`, then use the image name to be synchronized as title (**The image name needs to be a full name, which means `registry` and `tag` cannot be comitted**), the content of `issue` can be empty.

For example: open a new `issue` with title `k8s.gcr.io/kube-apiserver:v1.20.6`, Then the github action will automatically pull the image and push it to the [`mirrorgcrio` repository](https://hub.docker.com/u/mirrorgcrio/), then you can use `docker pull mirrorgcrio/kube-state-metrics:latest` command to pull the image.

You can view the synchronized docker images through the link below:

[https://hub.docker.com/u/mirrorgcrio](https://hub.docker.com/u/mirrorgcrio)

![](https://github.com/JaeGerW2016/mirror_gcrio2docker_image/blob/main/images/mirror_gcrio2docker_image.jpg)


## Customize ` action`

After `fork` this repository, check `issues` in `features` on the `Settings` page of the forked repository, then enable `GitHub actions` on the `Actions` page, add corresponding `secrets` as needed, then you can create `issue` in your forked repository to synchronize the docker image

## `secrets` supported by `action`

|         key         |                value                 |
| :-----------------: | :----------------------------------: |
|  `SOURCE_USERNAME`  |     username of source registry      |
|  `SOURCE_PASSWORD`  |     password of source registry      |
|  `TARGET_REGISTRY`  | target registry, default `docker.io` |
| `TARGET_REPOSITORY` |   target repository, default null    |
|  `TARGET_USERNAME`  |       username of `docker hub`       |
|  `TARGET_PASSWORD`  | password or `token` of `docker hub`  |

## If the source registry needs to log in

After `fork` this github repository, add the following `secrets`:

|        key        |                value                |
| :---------------: | :---------------------------------: |
| `SOURCE_USERNAME` |     username of source registry     |
| `SOURCE_PASSWORD` |     password of source registry     |
| `TARGET_USERNAME` |      username of `docker hub`       |
| `TARGET_PASSWORD` | password or `token` of `docker hub` |


**Remarks: If you log in with token on docker hub, you cannot modify the description of the synchronized docker images**

For details: [https://github.com/peter-evans/dockerhub-description/issues/10](https://github.com/peter-evans/dockerhub-description/issues/10)

## If the target registry is not `docker.io`

After `fork` this github repository, add the following `secrets`:

|         key         |               value                |
| :-----------------: | :--------------------------------: |
|  `TARGET_REGISTRY`  | target registry, such as `ghcr.io` |
| `TARGET_REPOSITORY` | target repository, such as `test`  |
|  `TARGET_USERNAME`  |    username of target registry     |
|  `TARGET_PASSWORD`  |    password of target registry     |

## Project stats

![Alt](https://repobeats.axiom.co/api/embed/11e8bb6f504f02fca58a38db2527c314b8a0b9c4.svg "Repobeats analytics image")
