# docker-compose-gpu

A minimal repository to **verify that NVIDIA GPUs are accessible via Docker Compose**.  
This project is intentionally simple and is only meant to answer one question:

> **Can Docker Compose see and use my GPU?**

If `nvidia-smi` works inside the container, your GPU setup is correct.

---

## What this repository does

- Starts a GPU-enabled container using **Docker Compose**
- Runs `nvidia-smi` inside the container
- Lets you quickly confirm whether:
  - NVIDIA Driver
  - NVIDIA Container Toolkit
  - Docker Compose GPU configuration  
  are working correctly

This is useful **before** setting up any ML / PyTorch / training environments.

---

## Requirements (Host)

- NVIDIA GPU
- NVIDIA Driver (GPU visible on host)
- Docker Engine
- Docker Compose v2 (`docker compose`, not `docker-compose`)
- NVIDIA Container Toolkit

First, make sure these commands work on the host:

```bash
nvidia-smi
docker run --rm --gpus all nvidia/cuda:12.4.1-base-ubuntu22.04 nvidia-smi
```
If this fails, the problem is not Docker Compose yet.

## Usage
1. Clone
```bash
git clone https://github.com/hisashi-ito/docker-compose-gpu.git
cd docker-compose-gpu
```

2. Start the container
```bash
docker compose up --build
```
If you see nvidia-smi output (GPU name, driver version, etc.), it works.
