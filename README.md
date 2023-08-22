# Streamr Open Data Challenge

## Overview

This project is part of my participation in the [LearnWeb3DAO Streamr Open Data Challenge](https://learnweb3.io/bounties/open-data-challenge-bounty/).

The goal of the challenge is creating a data stream on the decentralized Streamr Network and publish it on [The Hub](https://streamr.network/hub/projects).

## About Streamr

[Streamr](https://streamr.network/) is a fully decentralised and scalable protocol for many to many data pipelines, network analytics and instant messaging.

## What I created

For this challenge, I will create a Streamr data stream that delivers real-time price updates for Ethereum and Bitcoin in USD. The data will be sourced from [CoinGecko API](https://www.coingecko.com/en/api).
The stream will be set up to broadcast data at regular intervals, providing an up-to-date feed of the cryptocurrency prices.

### Streamr Stream Specifications

- Stream Name: BTC-ETH-USD-Price
- Streamr URL: `0x163b33c875cd58acaeb557fdc00e30e17f826730/btc-eth-usd-price`
- Frequency: Updated every 5 minutes
- Data Format: JSON
- Data Structure: `{ "bitcoin": {"usd":26004}, "ethereum": {"usd":1656.13}, "timestamp": 1692719868 }`

### Getting Started

To use this project, follow these steps:

1. Clone this repository to your local machine.
2. Set up your development environment by creating a `.env` file.
3. Run `npm install` to install required packages and dependencies.

### Files

1. **create-new-streamr.js**

This script creates a new stream on the Streamr Network and print the corresponding URL. This action requires MATIC Tokens for processing.

To run the script, execute the following command:

```bash
node create-new-streamr.js
```

**After running the script:**

- Go to the [Streamr Hub](https://streamr.network/hub/streams) and log in.
- Click on "Your streams" and click on your new streamr.
- Modify the access control settings to "Public".
- Set up data storage and specify the number of historical days.
- Save your changes.

Note: These actions will trigger transactions that incur a cost of 2-3 cents in MATIC Tokens.

2. **update-streamr.js**

This script retrieves data from the specified API and sends it to the Streamr stream.

To run the script, execute the following command:

```bash
node update-streamr.js
```

Remember to adjust any placeholders or details in the instructions to match your actual project setup.

## Extra: Webserver to host

To make the data updating process automated and accessible online, I've created a simple web server using Express with the `server.js` file. This server hosts the code that sends data to Streamr, and it can be accessed via an endpoint that triggers the data update.

### Accessing the Endpoint

The endpoint for triggering the data update is `/api/update-streamr`. However, access to this endpoint is restricted to a predefined list of allowed IP addresses for security reasons.

## Automating the Process with a Cron Job

To further streamline the data updating process, you can set up a cron job that periodically accesses the endpoint and triggers the script execution. This can be achieved by configuring a cron job to make a GET request to the endpoint URL at specified intervals.

### Example Cron Job:

```bash
*/5 * * * * curl -X GET "https://your-server.com/api/update-streamr"
```

## Contribute

If you would like to contribute to this project, feel free to submit a pull request. Contributions are welcome!

## License

This project is licensed under the [MIT License](LICENSE).
