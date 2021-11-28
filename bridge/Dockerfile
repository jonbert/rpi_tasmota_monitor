FROM python:3.10 AS build

WORKDIR /app

RUN pip --no-cache-dir install poetry

RUN poetry config virtualenvs.in-project true

COPY pyproject.toml poetry.lock ./

RUN poetry install --no-dev

COPY main.py ./

FROM python:3.10-slim AS runtime

WORKDIR /app
ENV PATH="/app/.venv/bin:$PATH"

COPY --from=build /app/ ./

CMD [ "python", "-u", "main.py" ]
