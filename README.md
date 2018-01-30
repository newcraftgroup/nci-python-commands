# nci-python-commands

Python commands is a light-weight, django-admin inspired, CLI Command tool.

# Usage

```sh
pip install nci-python-commands
manage
```

# List available commands
```sh
manage
```

# Run Commands
```sh
manage my-command-name
```

# Create Command

1. Create File

You can create a blank command by typing the following:
```sh
manage create_command
```

2. Example Code

In print_my_number.py:
```python
from commandable import Command


class PrintMyNumber(Command):
    description = "A description of your command"

    def __init__(self, args=None):
        self.register_argument(
            "-v",
            nargs='?',
            const=True,
            type=bool,
            description="Verbose output"
        )

        self.register_argument(
            "--mynumber",
            description="What is your number?",
            default=2,
            type=int
        )

        super().__init__(args)

    def command(self, **kwargs):
        # Place your command code here
        if self.get("v"):
            print("Verbose mode is on")

        print("Your lucky number is: {}".format(self.get("mynumber"))) #Your lucky number is: 2
```

# Hide Commands
```
class PrintMyNumber(Command):
    description = "A description of your command"

    hidden = True
...
```

# Adding existing commands to you configuration

In the section `Commands` add the module names that need to be scanned for commands and add a readable name as value.
```yaml
Commands:
  modulename: "module.path"
  downloaddata: "download.data"
  importers: "import_data"
```




