# Architecture for a formalized python client for the Cacophony Server (cacophony-api)

## Prior work
The following projects have code or test artifacts that are usable for adhoc access to the cacophony server through the REST API.
1) Python Classes in the test suite in [cacophony-api](https://github.com/TheCacophonyProject/cacophony-api). 
2) Python Classes in [cptv-download](https://github.com/TheCacophonyProject/cptv-download) 
3) Travis test and api test classes in [go-api](https://github.com/TheCacophonyProject/go-api)

##Goal 
Create a PyPi packaged python Cacophony Client for use against the Cacophony Project Server  for user and device contexts

## Proposed

### Naming: 

consider [pep-8 package and module names](https://www.python.org/dev/peps/pep-0008/#package-and-module-names) and [pep 432 Use a single name](https://www.python.org/dev/peps/pep-0423/#use-a-single-name)


>Package name: 
>>`thecacophonyproject.serverclient`, i.e. `from  thecacophonyproject.serverclient.{interface} import {interface-class}`

>Project name: 
>>`thecacophonyproject.serverclient`, i.e. `pip install thecacophonyproject.serverclient`


```python
from thecacophonyproject.serverclient.user import UserAPI  # user.py previously client.py
from thecacophonyproject.serverclient.device import DeviceAPI
from thecacophonyproject.serverclient.config import Config
```

### Testing:
Unittest with Travis CI, using both functional(mock server) and integration testing against current stable [cacophony-api](https://github.com/TheCacophonyProject/cacophony-api). Mimic the Influxdb client testing, Use Travis config from Cacophony [go-api](https://github.com/TheCacophonyProject/go-api)

Coverage Target 100% ?
TRAVIS CI testing runner: [nose2](https://docs.nose2.io/en/latest/index.html)

### Licensing


TODO: which licenses you use,  Cacophony-api, CPTV-download, and go-api all use something slightly different. I have not pushed to Github until this is sorted. Also would be good to confirm name I have named it for pypy as cacophony-client, python usage from CacophonyClient.client import CacophonyClient


>##### API server
>GNU AFFERO GENERAL PUBLIC LICENSE	
	Version 3, 19 November 2007
	Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/>
 **_From <https://github.com/TheCacophonyProject/cacophony-api/blob/master/LICENSE>_**


>#### CPTV-download
>GNU GENERAL PUBLIC LICENSE	
	Version 3, 29 June 2007
	Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/>
**_From <https://github.com/TheCacophonyProject/cptv-download/blob/master/LICENSE> _**

>#### go-api
>Apache License	
	Version 2.0, January 2004
	http://www.apache.org/licenses/
	TERMS AND CONDITIONS FOR USE, REPRODUCTION, AND DISTRIBUTION
**_From <https://github.com/TheCacophonyProject/go-api/blob/master/LICENSE> _**


### Contact

#####pypi setup.py and setup.cfg

TODO: Confirm contact details, license, author

```python
setup(
    name='TheCacophonyProject.ServerClient',
    version=version,
    description="Cacophony Project REST API client for python",
    long_description=readme,
    url='https://github.com/TheCacophonyProject/serverclient_python',
    license='GNU AFFERO GENERAL PUBLIC License 3 19 November 2007',
    packages=find_packages(exclude=['tests']),
    test_suite='nose2.collector.collector',
    # test_suite='tests',
    tests_require=test_requires,
    install_requires=requires,
    extras_require={'test': test_requires},

    # metadata to display on PyPI
    author="Anthony Uphof, Giampaolo Ferraro, Cameron Ryan-Pears, Menno Finlay-Smits",
    author_email="dev@cacphonyproject.org.nz",
    keywords="cacophonyproject api client rest",

    project_urls={
        "Bug Tracker": 'https://github.com/TheCacophonyProject/serverclient_python/issues',
        "Documentation": 'https://github.com/TheCacophonyProject/serverclient_python/wiki',
        "Source Code": 'https://github.com/TheCacophonyProject/serverclient_python',
    },

    classifiers=[
        'Development Status :: 1 - Alpha',
        'Intended Audience :: Developers',
        'License :: OSI Approved :: GNU AFFERO GENERAL PUBLIC License 3 19 November 2007',
        'Operating System :: OS Independent',
        'Programming Language :: Python',
        'Programming Language :: Python :: 3.6',
        'Programming Language :: Python :: 3.7',
        'Topic :: Software Development :: Libraries',
        'Topic :: Software Development :: Libraries :: Python Modules',
    ]
)
```


#### GITHUB 

CODEOWNERS
```text
* @mjs @auphofBSF @CameronRP @gferraro
```
