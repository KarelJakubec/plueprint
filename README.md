# plueprint
[API Blueprint](https://github.com/apiaryio/api-blueprint) parser written in Python.
It uses [Markdown](https://pythonhosted.org/Markdown) well-known package to do
initial DOM parsing.

### Installing
```
pip install plueprint
```

### Using
As a library:
```Python
from markdown import Markdown
m = Markdown(extensions=["plueprint"])
m.set_output_format("apiblueprint")
api = m.convert("""
FORMAT: 1A

# The Simplest API
This is one of the simplest APIs written in the **API Blueprint**.

# /message

## GET
+ Response 200 (text/plain)

        Hello World!
""")
print(api)
```
As a script:
```
python -m plueprint "Real World API.md"
python -m plueprint "Real World API.md" -o "api.pickle"
```

### Development
Fork and clone the repo, then submit pull requests.

#### Setup environment
```
cd plueprint
git submodule init
git submodule update

virtualenv env
. env/bin/activate
pip install -r requirements.txt

python ./setup.py install
```

#### Running test suite
```
python ./test.py
```

### Notes
To suppress warnings about parsed documents, set `plueprint.entities.report_warnings` to `False`.

Released under New BSD license.
