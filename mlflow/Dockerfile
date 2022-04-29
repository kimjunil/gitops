FROM python:3.9-slim-buster

ARG MLFLOW_VERSION=1.25.1

ENV BACKEND_STORE_URI ./mlruns
ENV DEFAULT_ARTIFACT_ROOT ./mlruns
ENV ARTIFACTS_DESTINATION ./mlartifacts
ENV HOST 0.0.0.0
ENV PORT 5000
ENV WORKERS 4
ENV EXPOSE_PROMETHEUS True

WORKDIR /mlflow/
RUN apt-get update && apt-get install libpq-dev python-dev gcc -y
RUN pip install --no-cache-dir mlflow==$MLFLOW_VERSION boto3 psycopg2
EXPOSE $PORT

ENTRYPOINT mlflow server \
    --default-artifact-root $DEFAULT_ARTIFACT_ROOT \
    --backend-store-uri $BACKEND_STORE_URI \
    --host $HOST \
    --port $PORT \
    --workers $WORKERS \
    --expose-prometheus $EXPOSE_PROMETHEUS
