# OpenTable-Reservation-Maker

The code that corresponds
with [this blog post on writing a script to make reservations for me on opentable](https://blog.jonlu.ca/wip/2021-12-03-opentable)

## Getting started

Python 3+ required

Install the dependencies

`pip install -r requirements.txt`

Set up the environment variables (section below)

Change the variables in `config.py`

Run the file

`python3 main.py`

## Usage

You must set up some environment variables first, and have some details about your OpenTable account beforehand.

| Variable             | Description                                                                                        | Required |
|----------------------|----------------------------------------------------------------------------------------------------|----------|
| BEARER_TOKEN         | Your bearer token from an intercepted OpenTable network request                                    | Yes      |
| FROM_PHONE_NUMBER    | The twilio number that will be sending the text notifications                                      |          |
| TO_PHONE_NUMBER      | The phone number that text messages will go to, and that is associated with your opentable account | Yes      |
| TWILIO_ACCOUNT_SID   | Twilio account SID                                                                                 |          |
| TWILIO_ACCOUNT_TOKEN | Twilio account token                                                                               |          |
| OPENTABLE_GPID       | Open table GID from a previous request                                                             | Yes      |
| OPENTABLE_DINERID    | Opentable diner id for your profile                                                                | Yes      |

## Config

`config.py` has the required configuration. I haven't added setup

## Monitoring

You can set up whatever preferred running solution you like. I set mine up with cron.

`crontab -e`

With an entry of

`* * * * * /usr/bin/python3 /home/jonluca/opentable/main.py`

You can set up your cron schedule how you'd like. I set mine up to check every
minute, [but you can use this tool to configure yours](https://crontab.guru/every-1-minute).

## Todo

- [ ] Authentication endpoint so that you don't need to already have your bearer token and diner ID
- [ ] Restaurant search so that you don't need to already know the ID of the restaurant you're looking for
- [ ] Deletion endpoint (Not sure if this is useful? But maybe if this turns into an API)
- [ ] Date exclusions - make it so that you can exclude specific dates that don't work
- [ ] Support multiple restaurants being watched at the same time
- [ ] Support restaurants that require a credit card
