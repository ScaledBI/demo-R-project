FROM rocker/r-base:4.1.2

RUN apt update \
    && apt-get install -y --no-install-recommends \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev

# install r-rmd dependencies from rocker/r-rmd
RUN apt update \
    && apt install -y --no-install-recommends \
    ghostscript \
    lmodern \
    pandoc-citeproc \
    qpdf \
    r-cran-formatr \
    r-cran-ggplot2 \
    r-cran-knitr \
    r-cran-rmarkdown \
    r-cran-runit \
    r-cran-testthat \
    r-cran-rjava \
    texinfo \
    texlive-fonts-extra \
    texlive-fonts-recommended \
    texlive-latex-extra \
    texlive-latex-recommended \
    texlive-luatex \
    texlive-plain-generic \
    texlive-science \
    texlive-xetex \
    && install.r binb linl pinp tint \
    && mkdir ~/.R \
    && echo _R_CHECK_FORCE_SUGGESTS_=FALSE > ~/.R/check.Renviron \
    && cd /usr/local/bin \
    && ln -s /usr/lib/R/site-library/littler/examples/render.r .

## Install additional dependencies
RUN install2.r --error \
    -r 'http://cran.rstudio.com' \
    tidyverse \
    plotly \
    DT \
    scales \
    remotes \
    && rm -rf /tmp/downloaded_packages/ /tmp/*.rds

WORKDIR /data
COPY . /data

CMD ["bash"]