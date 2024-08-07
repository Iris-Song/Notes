# Backend
## Token
### Handle token expire
if response return description like `token expire`, add `raise xxException`

In top module, add `try xxException` `catch`, in `catch`, get new token using `refresh_token`
