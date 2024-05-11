FROM python:3.6.0-alpine
RUN apk --no-cache add gcc musl-dev linux-headers

WORKDIR /app
ADD . /app

RUN pip install --trusted-host pypi.org --trusted-host pypi.python.org --trusted-host files.pythonhosted.org -r /app/requirements.txt && pip install Flask markupsafe==1.1.1

ENV POST_DATABASE_HOST post_db
ENV POST_DATABASE posts

CMD ["python3", "post_app.py"]