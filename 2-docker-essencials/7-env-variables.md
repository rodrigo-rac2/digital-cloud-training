## Simple app that uses an environment variable

```
import os
from flask import Flask

app = Flask(__name__)

color = os.environ.get('APP_COLOR')

@app.route("/")
def main():
  print(color)
  return render_template("hello.html", color=color)

if __name__ == "__main__":
  app.run(host="0.0.0.0", port="8080")
```

To run the container that invokes this app and set the `APP_COLOR` variable

> docker run -e APP_COLOR=blue my-simple-app-color

The list of environment variables are displayed in the `docker inspect`, under `Env`
