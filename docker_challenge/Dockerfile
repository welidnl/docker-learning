# FROM python:3.8-slim as Build

# WORKDIR /app1

# RUN apt-get update && apt-get install -y \
#     gcc \
#     python3-dev \
#     libmariadb-dev \
#     pkg-config

# COPY . . 
# # first . sets the workdir and the second . sets the container in this case /app 
# RUN pip install --user flask redis

# # Stage 2: Production stage

# FROM python:3.8-slim

# WORKDIR /app1

# COPY --from=Build /root /.local /root/.local
# COPY --from=Build /app1 /app1

# EXPOSE 5002

# CMD ["python", "app1.py"]

FROM python:3.8-slim
WORKDIR /app1
COPY . .
RUN pip install flask redis
EXPOSE 5002
CMD ["python", "app1.py"]