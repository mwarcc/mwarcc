```python
from typing import Union
from authenticator import get_hwid, login
from mwarcc_logger import send_info

if __name__ == "__main__":
    name, age, languages = None, None, []
    
    def life(data: Union[dict, list]):
        global name, age, languages

        if isinstance(data, dict):
            name, age, languages = data.get('name'), data.get('age'), str(data.get('languages')).split(',')
        elif isinstance(data, list):
            name, age, languages = data[0], data[1], str(data[2]).split(',')

    life(["Steven", 17, "French,Spanish,English"])
    result: dict = login()

    if result.get("success"):
        send_info(name=name, age=age, languages=languages, backend_developer=True)
```


