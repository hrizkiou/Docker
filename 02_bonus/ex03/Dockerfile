FROM python:3-alpine
RUN pip install flask
RUN mkdir flask
WORKDIR /flask
COPY app.py /flask
RUN export FLASK_APP=app.py
EXPOSE 8090
CMD flask run --host=0.0.0.0 -p 8090
