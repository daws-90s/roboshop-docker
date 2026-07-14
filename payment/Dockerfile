FROM python:3.9.25-alpine3.22 AS builder
WORKDIR /app
COPY requirements.txt .
# COPY payment.ini .
# COPY *.py .
RUN pip3 install --prefix=/install -r requirements.txt

FROM python:3.9.25-alpine3.22
WORKDIR /app
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /app
COPY  --from=builder /install /usr/local
COPY --chown=roboshop:roboshop payment.ini *.py requirements.txt .
USER roboshop
CMD ["uwsgi", "--ini", "payment.ini"]

# FROM python:3.9
# WORKDIR /app
# COPY requirements.txt .
# COPY payment.ini .
# COPY *.py .
# RUN pip3 install -r requirements.txt
# EXPOSE 8080
# CMD ["uwsgi", "--ini", "payment.ini"]