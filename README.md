Setting image Dockerfile untuk dideploy.
```text
FROM python:3.11-slim

ENV PYTHONUNBUFFERED True
ENV APP_HOME /app

WORKDIR $APP_HOME

COPY . ./

ENV PORT 1234
ENV MYSQL_URL "mysql+pymysql://root:PASSWORD@SERVER-IP:PORT/NAME DATABASE"
ENV JWT_SECRET_KEY "SECRET KEY"
ENV JWT_REFRESH_SECRET_KEY "REFRESH SECRET KEY"

RUN pip install --no-cache-dir -r requirements.txt

CMD exec uvicorn main:app --host 0.0.0.0 --port ${PORT}
```

![image](https://github.com/fikriiardiansyahh/fikri/assets/72667607/16f63ae3-093d-4cc8-9df4-4a56d92b9283)
