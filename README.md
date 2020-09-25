<p align="center"><a href="https://www.codechefvit.com" target="_blank"><img src="https://s3.amazonaws.com/codechef_shared/sites/all/themes/abessive/logo-3.png" title="CodeChef-VIT" alt="Codechef-VIT"></a>
</p>

# Office Panel and Github Leaderboard

A web application that shows various useful information for the office, like upcoming events and a leaderboard counting the number of Github commits.

<p align="center">
	<img src="http://i.imgur.com/Af0ESvZ.png" />
</p>

## Deploy

### Credentials
Either grab the `credentials.py` file from the [TechX Google Drive](https://drive.google.com/drive/folders/0B_1TM7HzBrvcTmwzMVQtWi1CN1k?usp=sharing), or follow the instructions below.

First create a `credentials.py` in the root directory of the project. The contents of the file look like this:
```python
# Github Token
token = ""

# Calendar
refresh_token = ""
client_id = ""
client_secret = ""
```
#### GitHub
The Github token can be obtained from any account with access to `ORG_NAME` by going to https://github.com/settings/tokens. Make sure to check the `repo` scope while issuing the token.

#### Calendar
The calendar fields can be obtained by first registering an app at the [Google Developer Console](https://console.developers.google.com/). This will give you the `client_id` and `client_secret`.

To obtain a refresh token, add https://developers.google.com/oauthplayground to the list of redirect URI's of your app. Then head over to the [Google OAuth Playground](https://developers.google.com/oauthplayground/), add the `https://www.googleapis.com/auth/calendar.readonly` in the list of scopes and hit Authorize API.

This needs to be done from a google account that has access to the `ORG_NAME` calendar. The click the `Exchange auth code for tokens` button and grab the `refresh_token`

### Running
Execute,
```
pip install -r requirements.txt
```
You may have to use system specific package managers to resolve a few dependancies. (For instance, you need to use fedora's package manager to get six.)

Then run,
```
python app.py
```

This app uses sticky sessions and a persistant background thread and storage. Use appropriate deployment methods. The default run uses Flask's internal wsgi server. You can use a production ready server like gunicorn with only a single worker thread as well,
```
gunicorn -w 1 -b 0.0.0.0:80 app:app
```

## License

[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)

<p align="center">
	With :heart: by <a href="https://www.codechefvit.com" target="_blank">CodeChef-VIT</a>
</p>
