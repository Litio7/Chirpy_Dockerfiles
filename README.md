# Dockerfiles to Work with jekyll theme chirpy

This repository provides two Docker environments to develop or test the [jekyll-theme-chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) theme locally.

## Ruby Slim Lightweight Environment (~1.33 GB)

A minimal Docker setup focused only on what’s strictly necessary to run the Jekyll site.

### Requirements

- [Docker](https://docs.docker.com/get-docker/).

### Setup

Clone the repository and build the image:

```bash
git clone https://github.com/Litio7/Chirpy_Dockerfiles.git
cd Chirpy_Dockerfiles/Light_Ruby_Slim

sudo docker build -f Dockerfile -t jekyll_chirpy_image .
```

Then run the container:

```bash
sudo docker run -dit --name jekyll_chirpy_container -p 4000:4000 jekyll_chirpy_image
```

Access the site at: `http://127.0.0.1:4000/`

This setup is intended for users who already have the theme or want a fast bootstrapped environment.

## Debian Bookworm Full Environment (~1.66 GB)

A fully-featured Docker environment built on Debian Bookworm. Useful for more complete workflows, including theme development and extended tooling.

### Requirements

- [Docker](https://docs.docker.com/get-docker/).
- [Nerd Fonts](https://www.nerdfonts.com/font-downloads).

### Setup

Clone the repository and build the image:

```bash
git clone https://github.com/Litio7/Chirpy_Dockerfiles.git
cd Chirpy_Dockerfiles/Full_Debian_Bookworm

sudo docker build -f Dockerfile -t jekyll_chirpy_image .
```

Run the container and open a shell:

```bash
sudo docker run -dit --name jekyll_chirpy_container -p 4000:4000 jekyll_chirpy_image

sudo docker exec -it jekyll_chirpy_container bash
```

Inside the container, start the Jekyll server:

```bash
bundle exec jekyll serve --watch --host 0.0.0.0
```

Then access the site at: `http://127.0.0.1:4000/`

This setup includes additional system packages and is more suitable for a development environment. Use `tmux` and `nvim` to work within it.

### Additional Tools

#### Favicon Generator

#### Metadata Cleaner

