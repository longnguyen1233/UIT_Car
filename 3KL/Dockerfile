FROM ubuntu:18.04

RUN : \
    && apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
        software-properties-common \
    && add-apt-repository -y ppa:deadsnakes \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
        python3.8-venv \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && :

RUN python3.8 -m venv /venv
ENV PATH=/venv/bin:$PATH

WORKDIR Car

COPY . .


RUN python3 -m pip install --upgrade pip && \
    python3 -m pip install -r requirements.txt

RUN apt update && apt install -y libsm6 libxext6 &&\
    apt-get install -y libxrender-dev
RUN apt install git -y\
    && cd \
    && git clone https://github.com/longnguyen1233/UIT_Car.git

CMD python3.7 ~UIT_Car/3KL/client.py
