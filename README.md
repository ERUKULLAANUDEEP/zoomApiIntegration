# zoomApiIntegration
  # Integration zoom into host app(documentation coding is pending)

                        *This is the High Level Overview*

              **CreateOauthApp**——>**Use generatedURL** —->**ZoomLogin** ——> 
  
    **RedirectstoConfiguredUrl**——>**Request Accesstoken** ——> **AccessAllZoomApi’s**(using accesstoken)

This is the documentation link which helped me in the given assessment       [https://marketplace.zoom.us/docs/guides/auth/oauth](https://marketplace.zoom.us/docs/guides/auth/oauth)
  I choosed to use oauth authentication as JWT is depricated

1. First thing need to create an app using zoom app market place where
the user needs to provide all the required details for the creation of an app
which in return generate you client id and secret along with  a url in this format(redirect url configured is “https://google.com”)
[https://zoom.us/oauth/authorize?client_id=i8bwQGxR_ONwr0dCynJw&response_type=code&redirect_uri=https%3A%2F%2Fgoogle.com](https://zoom.us/oauth/authorize?client_id=i8bwQGxR_ONwWr0dCynJw&response_type=code&redirect_uri=https%3A%2F%2Fgoogle.com)
2. let’s assume we had a login zoom button in our host application with the above link as soon as user hits the button, he will be forwarded to zoom login page and ones the user logins into zoom then he will be redirected to  configured url  (example https://google.com?code=’xyz’)
3. Ones the user logged in then he/she will be able to see create meetings button when user hits the button. will trigger an accesstoken api only at the first time which has the above code(in the above ex google url ).
4.  accesstoken api `[https://zoom.us/oauth/token](https://zoom.us/oauth/token)` which needs clientId,secret as authorisation and code which we got in redirected url is used as a parameter to get access token.
5. As soon as we get the access token we can create meeting with this api [https://api.zoom.us/v2/users/me/meetings](https://api.zoom.us/v2/users/me/meetings) sending access token as the authorisation

Please go through the screenshots which is step by step procudure which helped me in creating zoom meeting using the api
<img width="951" alt="code1" src="https://user-images.githubusercontent.com/39010804/179728776-ac0b154d-9f4d-4609-9609-203b1c827a75.png">
<img width="935" alt="code2" src="https://user-images.githubusercontent.com/39010804/179728783-57403a93-0c72-418a-aff1-a372db517ad9.png">
<img width="956" alt="code3" src="https://user-images.githubusercontent.com/39010804/179728795-1e9e9645-6285-479a-b06e-cb24a0ae3b2f.png">
<img width="953" alt="code4" src="https://user-images.githubusercontent.com/39010804/179728805-83ca556b-9858-4b99-95e7-703e616ff67d.png">
![code5](https://user-images.githubusercontent.com/39010804/179728813-79c55244-aad2-4c75-a8d3-9f705da0e474.png)
