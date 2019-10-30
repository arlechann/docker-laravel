# How to Use

Build images under the docker/* and exec next.

```sh
$ docker run --rm -v $(pwd):/app composer bash -c "cd /app; composer create-projct 'laravel/laravel' --prefer-dist' ."
$ docker-compose up -d
```
