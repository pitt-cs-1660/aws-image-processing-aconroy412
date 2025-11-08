FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

############
#
# TODO: implement the rest of the image

WORKDIR ${LAMBDA_TASK_ROOT}

COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

COPY pyproject.toml ./

RUN uv pip install --system -e .

COPY handler.py ./

CMD ["handler.greyscale_handler"]
#
############
