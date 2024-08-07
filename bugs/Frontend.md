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
- [not GET using request Body]( https://stackoverflow.com/questions/978061/http-get-with-request-body)
- use package capture to debug
- chrome package capture
  - Developer tool > Network
  - don't stop, copy cURL, then import in Postman
- mock response
  - Swagger[https://reeli.github.io/blog/tools_swagger-to-mocks.html#%E5%A4%84%E7%90%86-swagger-json]
  - bifrost bytedance
- JavaScript big number lost precision
  - backend use `string`
  - API platform define type as `string`, and
  
    ```
    x-open-format:
      type: string
    ```

## React
+ `useEffect` happens after component mount
+ redirect before the page rendered
  ```
  if (...) {
    window.location.href = 'xxxx'
  } else {
    ReactDOM.render(
      <App />

      document.getElementById('root')
    )
  }
  ``` 
+ `useCallback`