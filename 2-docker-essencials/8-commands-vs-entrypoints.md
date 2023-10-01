## Commands can be passed upon bringing the containers up

> docker run <image> [COMMAND]

> docker run ubuntu sleep 10

## How to make this change permanent in an image (always run the sleep command)

```
FROM Ubuntu

CMD sleep 10
```

there are possible formats

> CMD ["command, "param"]
 
or

> CMD command param1

```
FROM Ubuntu

CMD ["sleep","5"]
```

if the user runs `docker run ubuntu-sleeper`, it will sleep for 5 seconds. 
if the user runs `docker run ubuntu-sleeper sleep 10`, any additiional COMMAND provided will replace whatever is defined on CMD.
and sometimes it doesn't look intuitive... 

## If we want to parametrize the command, we need to use ENTRYPOINT

```
FROM Ubuntu

ENTRYPOINT ["sleep"]
```

then

> docker run ubuntu-sleeper 10

However, this will return an error if no param is provided

## If we need to give the user the option of getting a default value, so they can run `docker run ubuntu-sleeper` and not get an error, we should use ENTRYPOINT and CMD together

```
FROM Ubuntu

ENTRYPOINT ["sleep"]

CMD ["10"]
```

This way, `docker run ubuntu-sleeper` will sleep for 10 seconds by default, but any number passed to the CLI will replace the CMD instruction, like `docker run ubuntu-sleeper 100` - that would sleep for 100 seconds.


## Is it possible to replace the entrypoint, though?

> docker run --entrypoint sleep2.0 ubuntu-sleeper 10
