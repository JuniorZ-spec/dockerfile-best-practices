FROM python:3.12-slim AS build
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir --user -r requirements.txt

FROM python:3.12-slim
RUN useradd -m app
WORKDIR /app
COPY --from=build /root/.local /home/app/.local
COPY . .
ENV PATH=/home/app/.local/bin:$PATH
USER app
EXPOSE 8000
CMD ["python", "-m", "app"]
