# Docker PHP image with various extensions

**Master** branch is only for summary, visit each branch for detail

## Docker Hub

[![Repo](https://img.shields.io/badge/repo-fatindeed%2Fphp-blue.svg)](https://hub.docker.com/r/fatindeed/php/) [![Docker Stars](https://img.shields.io/docker/stars/fatindeed/php.svg)](https://hub.docker.com/r/fatindeed/php/) [![Docker Pulls](https://img.shields.io/docker/pulls/fatindeed/php.svg)](https://hub.docker.com/r/fatindeed/php/) [![Docker Automated build](https://img.shields.io/docker/automated/fatindeed/php.svg)](https://hub.docker.com/r/fatindeed/php/) [![Docker Build Status](https://img.shields.io/docker/build/fatindeed/php.svg)](https://hub.docker.com/r/fatindeed/php/)

## Tags

- ![Tag](https://img.shields.io/badge/tag-fatindeed%2Fphp%3Aimagick-blue.svg) ![MicroBadger Size](https://img.shields.io/microbadger/image-size/fatindeed/php/imagick.svg) ![MicroBadger Layers](https://img.shields.io/microbadger/layers/fatindeed/php/imagick.svg) ([imagick/Dockerfile](https://raw.githubusercontent.com/fatindeed/docker-php/master/imagick/Dockerfile))
- ![Tag](https://img.shields.io/badge/tag-fatindeed%2Fphp%3Apcntl-blue.svg) ![MicroBadger Size](https://img.shields.io/microbadger/image-size/fatindeed/php/pcntl.svg) ![MicroBadger Layers](https://img.shields.io/microbadger/layers/fatindeed/php/pcntl.svg) ([pcntl/Dockerfile](https://raw.githubusercontent.com/fatindeed/docker-php/master/pcntl/Dockerfile))
- ![Tag](https://img.shields.io/badge/tag-fatindeed%2Fphp%3Astats-blue.svg) ![MicroBadger Size](https://img.shields.io/microbadger/image-size/fatindeed/php/stats.svg) ![MicroBadger Layers](https://img.shields.io/microbadger/layers/fatindeed/php/stats.svg) ([stats/Dockerfile](https://raw.githubusercontent.com/fatindeed/docker-php/master/stats/Dockerfile))
- ![Tag](https://img.shields.io/badge/tag-fatindeed%2Fphp%3Ayaf-blue.svg) ![MicroBadger Size](https://img.shields.io/microbadger/image-size/fatindeed/php/yaf.svg) ![MicroBadger Layers](https://img.shields.io/microbadger/layers/fatindeed/php/yaf.svg) ([yaf/Dockerfile](https://raw.githubusercontent.com/fatindeed/docker-php/master/yaf/Dockerfile))
- ![Tag](https://img.shields.io/badge/tag-fatindeed%2Fphp%3Ayaml-blue.svg) ![MicroBadger Size](https://img.shields.io/microbadger/image-size/fatindeed/php/yaml.svg) ![MicroBadger Layers](https://img.shields.io/microbadger/layers/fatindeed/php/yaml.svg) ([yaml/Dockerfile](https://raw.githubusercontent.com/fatindeed/docker-php/master/yaml/Dockerfile))

## Tips

1.  使用 *Alpine Linux* 镜像

    在build时传入`ALPINE_MIRROR`参数

    ```sh
    docker build --build-arg ALPINE_MIRROR=https://mirrors.aliyun.com -t myimage .
    ```

2.  新分支

    ```sh
    git checkout --orphan <new_branch>
    ```
