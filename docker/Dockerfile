FROM python:3.8-slim-buster

RUN groupadd -g 1234 appuser && \
    useradd -r -u 1234 -g appuser appuser

COPY application /opt/application

RUN pip3 install --no-cache-dir -r /opt/application/requirements.txt

RUN find / -perm /6000 -type f -exec chmod a-s {} \; || true

USER appuser

EXPOSE 5000

ENTRYPOINT [ "python3", "/opt/application/server.py" ]
