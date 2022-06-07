# NBN-Py

This package provides an unofficial wrapper of the National Broadband Network's (NBN) API. It allows you to programatically lookup address's and examine connection details such as the connection type (FTTP, HFC, etc), service type, connection status and more.
<br/><br/>
**Disclaimer:** _This project is not affiliated with Nox, and not an official Nox plugin._


## Installation

Install `nbnpy` from the Python Package Index:

```console
$ pip install nbn
```

## Requirements

- Python 3.8+


## Usage

This example gets the LocationID for an address then looks up the NBN connection details for it.
```python
import pprint
from nbnpy.nbn import NBN

nbn_client = NBN()
location_ids = nbn_client.get_location_ids_from_address("1 Flinders Street, Melbourne VIC")

# The "get_location_ids_*" methods return a list of nearby locations
# For the purpose of this example, the first result will suffice
location_id = location_ids["suggestions"][0]["id"]

location_info = nbn_client.location_information(location_id)
pprint.pprint(location_info)
```

## Building the Project

This package uses `poetry` and `nox` for package management and building. 

If nox is not already installed, install it:
```console
$ pip install nox
```

Run everything including tests and documentation building
```console
$ nox

# Or to run a specific stage:
$ nox -s <stage name>, eg
$ nox -s tests
```


## Issues

If you encounter any problems,
please [file an issue](https://github.com/diabolical-ninja/nbn/issues) along with a detailed description.
