# Hydra Modules
Finding a login page is very good. This means that we can try to log-in and then attempt to get shells through the user's account. It is even better if you can get admin credentials.

## Login.php
With these pages, the first thing to do is to try the top 10 admin credentials:
i.e. `admin:admin`

If none of these are able to get us access, then we can try noisier, more widespread attack methods called `password spraying`. This attack uses old, already found, guessed, or decryptred passwords


## Brute Forcing Forms
Hydra has the ability to be used in many different ways, including brute forcing forms. As we are 'trying' to brute force our way into a login form with the extension`.php`, we should try using the `http[s]-post-form` supplied by Hydra.

The first thing that needs to be done is:
- Determine whether submitting the form sends a `GET` or `POST` request

--> Note: you can tell by whether the parameters are inputted into the URL or not. If they are, it will be a `GET` form.

To use the `http[s]-post-form` you would need to use this syntax:
```
<URL path> <parameters> <failed / successful login string>

E.g.

/login.php:[user parameter]=^USER^&[password parameter]=^PASS^:[FAIL/SUCCESS]=[success/failed string]
```

--> In the example, we don't know what the fail / success login string is.

### Fail / Success String

There are two types of flags that you can use for the fail / success string.
1. `F="html_string"` --> hydra will keep looking until the string is *not found* in the response
2. `S="html_string"` --> hydra will keep looking until this string _is found_ in the response

As we don't know what the success / fail string is like, we have to find something else to put into the `<failed / successful login string>` section. In our case, as the page which we use to input the login credentials is called `Admin Panel` we can use `Admin Panel` as the false string.

Another thing we can use is the html used to render the page. We can very safely assume that once we manage to log in, the HTML used to render the login page will not be there anymore. Therefore we can also use:

```
"/login.php:[user parameter]=^USER^&[password parameter]=^PASS^:F=<form name='login'"

```
