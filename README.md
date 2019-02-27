# chainsaw_client

import requests


url_base = 'http://127.0.0.1:5000/chainsaw_API/chainsaw'

weather_data = {'name': 'Temperature', 'catches': 6, 'country': 'USA'}
response = requests.post(url_base, data=weather_data)
if response.status_code == requests.codes.created:
    print('Temperature record created')
else:
    response.raise_for_status()  # Raises exception


# Get all records
response = requests.get(url_base)
print(response.json(), response.status_code)
if response.status_code == requests.codes.ok:
    data = response.json()
    for index, record in enumerate(data):
        print(index, record)

else:
    response.raise_for_staus()

# Delete record 2
response = requests.delete(f'{url_base}/2')
if response.status_code == requests.codes.ok:
    print('record 2 deleted')
else:
    response.raise_for_staus()




