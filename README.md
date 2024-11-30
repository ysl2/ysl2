# My workflow: dotfiles + nvim

## Try it in docker

1. Download docker mirror:

    ```bash
    docker pull ysl2/ysl2:latest
    ```

2. Go to the env.

    ```bash
    docker run \
        -it \
        --rm \
        -w /root \
        ysl2/ysl2:latest \
        zsh
    ```

3. If you only want to use nvim, try this:

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
