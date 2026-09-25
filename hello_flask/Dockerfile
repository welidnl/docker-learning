# FROM python:3.8-slim
# WORKDIR /app
# COPY . .
# RUN apt-get update && apt-get install -y \
#     gcc \
#     python3-dev \
#     libmariadb-dev \
#     pkg-config
# RUN pip install flask mysqlclient
# EXPOSE 5002
# CMD ["python", "app.py"]

# Multi staging dockerfile to make it more efficient and smaller in size
# stage 1: Build stage

FROM python:3.8-slim as Build

WORKDIR /app

RUN apt-get update && apt-get install -y \
    gcc \
    python3-dev \
    libmariadb-dev \
    pkg-config

COPY . . 
# first . sets the workdir and the second . sets the container in this case /app 
RUN pip install flask mysqlclient

# Stage 2: Production stage

FROM python:3.8-slim

WORKDIR /app

COPY --from=Build /app /app

EXPOSE 5002

CMD ["python", "app.py"]