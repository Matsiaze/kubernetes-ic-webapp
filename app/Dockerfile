FROM python:3.6-alpine
ENV ODOO_URL="https://www.odoo.com/" \
    PGADMIN_URL="https://www.pgadmin.org/"
WORKDIR /opt
COPY . .
RUN pip install flask==1.1.2
EXPOSE 8080
ENTRYPOINT ["python", "app.py"]
