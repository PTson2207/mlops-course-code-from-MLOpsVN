FROM python:3.8-slim AS build

RUN apt-get update

RUN python -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"
RUN pip install --upgrade pip

COPY deployment/requirements.txt .
RUN pip install -r requirements.txt

FROM python:3.8-slim

COPY --from=build /opt/venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"
COPY . /model_serving
WORKDIR /model_serving