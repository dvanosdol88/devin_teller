# Teller Examples

## Introduction

This repository contains a small web front-end that allows easy interaction with Teller Connect and Teller's API via a back-end written in one of many languages. It can also serve as a starting point for your Teller integration.

## Set-Up

The only general dependency for the project is `python` version `3+`. Go ahead and clone the repository on your local machine. Based on the language you want to use for your back-end, visit the language's folder `README.md` for further instructions. Once the back-end is running locally, proceed to starting the static file server for the front-end application. Open the `static/index.js` file and fill the value associated to the `APPLICATION_ID` constant which appears at the top of the file with your Teller application's ID. If you are not sure what it is, visit [this page](https://teller.io/settings/application) to find it. You can also change the `ENVIRONMENT` based on whether you want to target real (`development`, `production`) or fake (`sandbox`) bank accounts. Save the file then run: 
```
$ ./static.sh
```

This will start a simple HTTP server listening on `:8000`. You can now visit [localhost:8000](http://localhost:8000) in your browser and start using the application.

### Certificate Configuration

For `development` and `production` environments, you need to configure TLS certificates for mTLS authentication with the Teller API. Set the following environment variables:

- `TELLER_CERT_PATH`: Absolute path to your TLS certificate file (e.g., `/path/to/cert.pem`)
- `TELLER_KEY_PATH`: Absolute path to your private key file (e.g., `/path/to/private_key.pem`)

Example usage:
```bash
export TELLER_CERT_PATH=/mnt/d/Projects/devin_teller/python/cert.pem
export TELLER_KEY_PATH=/mnt/d/Projects/devin_teller/python/private_key.pem

# Start backend from project root
cd /path/to/devin_teller
python python/teller.py --environment development
```

You can manage your certificates on the [Teller developer dashboard](https://teller.io/settings/certificates).

**Note:** Certificate files (*.pem, *.key) are excluded from version control for security.

## Usage

Use the *Connect* button on the top-right of the screen to enroll a new user. Upon completion, you will see the list of bank accounts on the page. You can interact with them by requesting their details, balances and transactions from Teller.

The *User* specified on the right-hand side is the Teller identifier associated to the user whose accounts were enrolled. The *Access Token* authorizes your Teller application to access the user's account data. For more information you can read our online [documentation](https://teller.io/docs).
