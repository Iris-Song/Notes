# Frontend
- post body type
  - form data
    ```
    const formData = new FormData();
    formData.append('username', emailValue);
    formData.append('password', passwordValue);

    axios
      .post(YOUR_API,
        formData,
        {
          headers: {
            //...
          },
          withCredentials: //..,
        }
      )
      .then((response) => {
        // ...
      })
    ``` 
  - raw(json)
    ```
    axios
      .post(YOUR_API,
        {
          id: id,
        },
        {
          headers: {
            //...
          },
          withCredentials: //..,
        }
      )
      .then((response) => {
        // ...
      })
    ```
  