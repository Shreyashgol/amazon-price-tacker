# Amazon Price Tracker

A Python-based price monitoring tool that tracks Amazon product prices and sends email notifications when prices drop.

## Overview

This script monitors a specific Amazon product's price at regular intervals and automatically sends an email alert whenever the price decreases. It's useful for tracking deals on items you're interested in purchasing.

## Features

- **Automated Price Monitoring**: Checks product prices at regular intervals (approximately 12 hours)
- **Price Drop Detection**: Identifies when prices decrease compared to the previous check
- **Email Notifications**: Sends email alerts with price drop details
- **Price History**: Maintains a list of historical prices for comparison

## Requirements

- Python 3.x
- `beautifulsoup4` - For HTML parsing
- `urllib` - For fetching web pages (built-in)
- `smtplib` - For sending emails (built-in)

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd amazon-price
```

2. Install required dependencies:
```bash
pip install beautifulsoup4
```

## Configuration

Before running the script, you need to configure the following:

1. **Product URL**: Update the `url` variable in `check_price()` function with your target Amazon product link

2. **Email Credentials**: In the `send_email()` function call at the bottom, provide:
   - `sender_email` - Your Gmail address
   - `sender_password` - Your Gmail app password (not your regular password)
   - `receiver_email` - Email address to receive notifications

3. **Check Interval**: Modify `time.sleep(43000)` to adjust the checking frequency (value in seconds)
   - Current: ~12 hours (43000 seconds)
   - Example: 3600 seconds = 1 hour

## Usage

Run the script:
```bash
python main.py
```

The script will:
1. Fetch the current price from Amazon
2. Compare it with the previous price (if available)
3. Send an email notification if the price has decreased
4. Wait for the specified interval before checking again
5. Repeat indefinitely

## How It Works

1. **check_price()**: Scrapes the Amazon product page and extracts the current price
2. **send_email()**: Sends an email notification via Gmail SMTP
3. **price_decrease_check()**: Compares current price with previous price to detect drops
4. **Main Loop**: Continuously monitors the price at set intervals

## Important Notes

- **Gmail Setup**: If using Gmail, enable "Less secure app access" or use an [App Password](https://support.google.com/accounts/answer/185833)
- **Amazon Terms**: Ensure web scraping complies with Amazon's Terms of Service
- **HTML Structure**: The script relies on Amazon's HTML structure. Changes to Amazon's website may require updates to the parsing logic
- **Price Format**: Currently configured for Indian Amazon (₹ currency)

## Troubleshooting

- **Connection Errors**: Check your internet connection and the product URL
- **Email Not Sending**: Verify Gmail credentials and ensure "Less secure app access" is enabled
- **Price Not Found**: Amazon's HTML structure may have changed; update the `find()` selector accordingly

## Future Improvements

- Support for multiple products
- Configurable price drop threshold
- Database storage for price history
- Web interface for configuration
- Support for other e-commerce platforms

## License

This project is open source and available for personal use.
