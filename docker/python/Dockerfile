FROM python:3.7

LABEL version="1.0"
LABEL maintainer="Yuto Chikazawa <minet6759@gmail.com>"
LABEL description="python-docker-template"

ENV PYTHONUNBUFFERED=1

RUN apt-get update -y --fix-missing \
    && apt-get install -y --no-install-recommends \
    sudo \
    vim \
    git \
    make \
    curl \
    wget \
    less \
    locales

WORKDIR /usr/src/source

ENV PIPENV_VENV_IN_PROJECT=1

COPY ./source/Pipfile  ./

RUN pip install --upgrade pip \
    && pip install pipenv \
    && pipenv install --skip-lock --system --dev

EXPOSE 8888

CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--allow-root", "--NotebookApp.token="]
