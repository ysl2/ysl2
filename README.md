# My workflow: dotfiles + nvim

## Try it in docker

1. Download docker mirror:

    ```bash
    docker pull ysl2/ysl2:latest
    ```

1. Go to the env.

    ```bash
    docker run \
        -it \
        --rm \
        -w /root \
        ysl2/ysl2:latest \
        zsh
    ```

1. If you only want to use nvim, try this:

    ```bash
    # For example, you want to edit your project `~/.config/nvim`:
    docker run \
        -it \
        --rm \
        -e PATH=/root/.vocal/_:/root/.vocal:/root/.vocal/nvim-linux64/bin:/root/.vocal/node-v22.11.0-linux-x64/bin:/root/.vocal/go/bin:/root/.cargo/bin:/root/.local/bin:/root/bin:/usr/sbin:/sbin:/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:/usr/local/sbin:/usr/local/bin:/usr/bin:/bin:/root/.vocal/go/gopath/bin: \
        -v ~/.config/nvim:/root/myproject \
        -w /root/myproject \
        ysl2/ysl2:latest \
        nvim
    ```

1. How to hot update in container:

    ```bash
    docker run \
        -it \
        -v ~/.ssh/id_rsa:/root/.ssh/id_rsa \
        -v ~/.ssh/id_rsa.pub:/root/.ssh/id_rsa.pub \
        -w /root \
        ysl2/ysl2:latest \
        zsh
    ```

1. (For myself) How to push changes to the docker hub:

    ```bash
    # Start the container, and modify something
    docker run -it ysl2/ysl2:v0.1.1 /usr/bin/zsh

    # Publish changes:
    docker commit 7b7f9d12db29 ysl2/ysl2:v0.1.2
    docker tag ysl2/ysl2:v0.1.2 ysl2/ysl2:latest
    docker push ysl2/ysl2:v0.1.2
    docker push ysl2/ysl2:latest
    ```
