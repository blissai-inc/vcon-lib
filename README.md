# vCon Python Library

This Python library provides a convenient way to work with vCon (Virtualized Conversation) objects. vCon is a standard for representing conversation data, including metadata, dialog, analysis, and attachments.

## Features

- Create and manipulate vCon objects
- Add parties, dialogs, attachments, and analysis to vCons
- Sign and verify vCons using JWS (JSON Web Signature)
- Generate UUID8 identifiers
- Pack and unpack dialogs
- Add and retrieve tags

## Installation

To install the vCon library, use pip:

```
pip install vcon
```

## Usage

Here's a quick example of how to use the vCon library:

```python
from vcon import Vcon

# Create a new vCon
vcon = Vcon.build_new()

# Add a party
vcon.add_party({
    "name": "Alice",
    "tel": "+1234567890"
})

# Add a dialog
vcon.add_dialog({
    "type": "text",
    "start": "2023-06-01T10:00:00Z",
    "parties": [0],
    "body": "Hello, world!",
    "encoding": "none"
})

# Add an attachment
vcon.add_attachment(
    body={"key": "value"},
    type="json_data",
    encoding="json"
)

# Add analysis
vcon.add_analysis(
    type="sentiment",
    dialog=[0],
    vendor="AnalysisCompany",
    body={"sentiment": "positive"},
    encoding="json"
)

# Add a tag
vcon.add_tag("importance", "high")

# Sign the vCon
private_key, public_key = Vcon.generate_key_pair()
vcon.sign(private_key)

# Verify the signature
is_valid = vcon.verify(public_key)

# Convert to JSON
json_string = vcon.to_json()

# Create a vCon from JSON
new_vcon = Vcon.build_from_json(json_string)
```

## API Reference

For detailed information about the available methods and their usage, please refer to the docstrings in the source code.

## Contributing

Contributions to the vCon library are welcome! Please submit pull requests or open issues on the GitHub repository.

## License

This project is licensed under the MIT License:

MIT License

Copyright (c) 2023 Thomas McCarthy-Howe

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Contact

For questions or support, please contact:

Thomas McCarthy-Howe
Email: ghostofbasho@gmail.com