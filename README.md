# Introduction

This is a project that can be used as a template to create a new Trame application.
It has a couple of tabs with input fields, example how to interact with Galaxy instance, 
upload and download configuration.


## Install dependencies  

```
poetry install
```

## Run

```bash
poetrty start run
```

## Develop

Run `poetry env info  --path` to see the path to Poetry environment. It can then be used
to configure your IDE to select the correct Python interpreter.

## Docker
### Build the image

without conda and mantid:

```bash
docker build -f dockerfiles/Dockerfile -t app .
```

with conda and mantid

```bash
docker build --build-arg BUILD_ENV=conda -f dockerfiles/Dockerfile -t app .
```

### Run the container

```
docker run -p 8081:8081 -it -e EP_PATH=/app app bash -c "/prepare_nginx.sh && python -m template_app.app --host 0.0.0.0 --server"  
```

then open your browser at http://localhost:8081/app/