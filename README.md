# API-s-using-python
# API-s-using-python
import requests
import json
from rest_framework import status

# The base URL for the API
BASE_URL = "https://jsonplaceholder.typicode.com/posts"

def perform_api_operations():
    # --- 1. GET Request (Retrieve Data) ---
    print("--- GET Request ---")
    response_get = requests.get(f"{BASE_URL}/1")
    if response.status_code == status.HTTP_200_OK:
        print("Success!")
        print(response_get.json())
    else:
        print(f"Error: {response_get.status_code}")

    print("\n")

    # --- 2. POST Request (Create Data) ---
    print("--- POST Request ---")
    new_data = {
        "title": "Learning Python APIs",
        "body": "This is a post created via the requests library.",
        "userId": 1
    }
    # headers tell the server what kind of data we are sending
    headers = {"Content-type": "application/json; charset=UTF-8"}
    
    response_post = requests.post(BASE_URL, data=json.dumps(new_data), headers=headers)
    print(f"Status Code: {response_post.status_code}")
    print(f"Response: {response_post.json()}")

    print("\n")

    # --- 3. PUT Request (Update Data) ---
    print("--- PUT Request ---")
    updated_data = {
        "id": 1,
        "title": "Updated Title",
        "body": "The body has been changed.",
        "userId": 1
    }
    response_put = requests.put(f"{BASE_URL}/1", data=json.dumps(updated_data), headers=headers)
    print(f"Status Code: {response_put.status_code}")
    print(f"Response: {response_put.json()}")

    print("\n")

    # --- 4. DELETE Request (Remove Data) ---
    print("--- DELETE Request ---")
    response_delete = requests.delete(f"{BASE_URL}/1")
    print(f"Status Code: {response_delete.status_code} (Success)")

if __name__ == "__main__":
    perform_api_operations()
    

