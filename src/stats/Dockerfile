FROM r-base

RUN apt update && apt upgrade -y
RUN apt install -y libpq-dev python3-pip python3-dev vim 

RUN pip install "yandex-pgmigrate==1.0.5"

WORKDIR /srv

## create directories
RUN mkdir -p data
RUN mkdir -p code/R
RUN mkdir -p code/python
RUN mkdir -p output

## install and cache R-packages
COPY R/install_packages.R code/R/
RUN Rscript code/R/install_packages.R

COPY . code/

# FIXME this must run on application start, not build time
#RUN pgmigrate -c "host=postgres dbname=sormas_stats user=stats_user password=password" -t latest migrate

#CMD Rscript code/main.R
CMD ["sh", "-c", "tail -f /dev/null"]