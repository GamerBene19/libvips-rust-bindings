# (c) Copyright 2019-2023 OLX
FROM rust:1.73.0-alpine3.18

ENV VIPS_VERSION=8.14.5

RUN apk add --update --no-cache \
            build-base \
            pkgconfig \
            meson \
            clang \
            clang-libclang \
            cgif-dev \
            expat-dev \
            fftw-dev \
            giflib-dev \
            glib-dev \
            gobject-introspection-dev \
            lcms2-dev \
            libexif-dev \
            libgsf-dev \
            libheif-dev \
            libimagequant-dev \
            libjpeg-turbo-dev \
            libpng-dev \
            librsvg-dev \
            libwebp-dev \
            openssl-dev \
            orc-dev \
            pango-dev \
            tiff-dev && \
    rustup component add rustfmt

RUN wget https://github.com/libvips/libvips/releases/download/v${VIPS_VERSION}/vips-${VIPS_VERSION}.tar.xz && \
    mkdir vips && \
    tar xvf vips-${VIPS_VERSION}.tar.xz -C vips --strip-components 1

WORKDIR /vips

RUN meson setup build --prefix /usr/ && cd build && meson compile && meson test && meson install
