#--- Debian Bookworm

FROM debian:bookworm

LABEL maintainer="github.com/litio7" \
      description="Debian Bookworm Full"

#--- Dependencies

RUN apt-get update && apt-get install -y \
    build-essential procps wget net-tools \
    libffi-dev libgdbm-dev libncurses5-dev libsqlite3-dev \
    ruby-full ruby-dev \
    python3 nodejs npm \
    git subversion \
    neovim tmux \
    locales && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

#--- Env

RUN sed -i 's/# *\(en_US.UTF-8 UTF-8\)/\1/' /etc/locale.gen && \
    locale-gen en_US.UTF-8

ENV TERM=xterm-256color \
    LANG=en_US.UTF-8 \
    LC_ALL=en_US.UTF-8

#--- Nvim

RUN wget https://github.com/neovim/neovim/releases/download/v0.11.1/nvim-linux-x86_64.tar.gz -O /opt/nvim.tar.gz && \
    tar -xzf /opt/nvim.tar.gz -C /opt/ && \
    rm /opt/nvim.tar.gz && \
    ln -s /opt/nvim-linux-x86_64/bin/nvim /usr/local/bin/nvim

#--- NvChad

RUN git clone https://github.com/NvChad/starter /root/.config/nvim && \
    nvim --headless -c 'MasonInstall lua-language-server' -c 'qa' && \
    sed -i '/load luasnips + cmp related in insert mode only/,+44d' /root/.local/share/nvim/lazy/NvChad/lua/nvchad/plugins/init.lua

#--- Tmux

RUN mkdir -p /root/.config/tmux && \
    wget https://raw.githubusercontent.com/gpakosz/.tmux/refs/heads/master/.tmux.conf -O /root/.config/tmux/tmux.conf && \
    wget https://raw.githubusercontent.com/gpakosz/.tmux/refs/heads/master/.tmux.conf.local -O /root/.config/tmux/tmux.conf.local

#--- GitPage

WORKDIR /root/jekyll-theme-chirpy

RUN git clone https://github.com/cotes2020/jekyll-theme-chirpy.git /root/jekyll-theme-chirpy && \
    git config --global user.email "build@example.com" && \
    git config --global user.name "Litio7"

#--- Gems

RUN gem install bundler jekyll && \
    ./tools/init.sh && \
    bundle install

#--- Server Port

EXPOSE 4000

