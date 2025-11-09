FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

############
#
# TODO: implement the rest of the image

FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

# set working directory
WORKDIR ${LAMBDA_TASK_ROOT}

# copy project requirements
COPY pyproject.toml ${LAMBDA_TASK_ROOT}/

# sync project and install dependencies
RUN uv sync --system -e .

# copy Lambda handler code
COPY handler.py ${LAMBDA_TASK_ROOT}/

# set PYTHONPATH to include virtual environment site-packages
ENV PYTHONPATH="${LAMBDA_TASK_ROOT}/.venv/lib/python3.13/site-packages"

# set the CMD to your handler function
CMD ["handler.resize_handler"]

#
############
