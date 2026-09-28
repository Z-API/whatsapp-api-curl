# Z-API — WhatsApp API Examples with PHP and cURL

Explore WhatsApp integrations with Z-API using PHP's cURL extension. Browse request examples and adapt them to your own application.

**[Explore the Examples](./curl.txt)** · **[Read the Documentation](https://developer.z-api.io)**

## About This Repository

The examples are collected in `curl.txt`, alongside sample responses and notes in Portuguese.

These are individual PHP snippets, not a standalone application or a shell script.

## What's Included

Examples cover:

- QR code retrieval.
- Sending audio, video, documents, and links.
- Marking messages as read.
- Publishing text and image status updates.
- Retrieving chats and contacts.
- Checking whether a phone number has WhatsApp.
- Creating groups and managing group administrators.

Refer to the current documentation for endpoint availability and request requirements.

## Prerequisites

- PHP with the cURL extension enabled.
- A [Z-API account](https://z-api.io).
- Your Z-API instance credentials.
- A connected WhatsApp instance for operations that require it.

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/Z-API/whatsapp-api-curl.git
cd whatsapp-api-curl
```

You can also open [`curl.txt`](./curl.txt) directly on GitHub.

### 2. Choose an example

Find the endpoint you want to explore in `curl.txt`.

Copy only its PHP code into a separate file, such as `example.php`. Exclude endpoint headings, sample responses, and explanatory notes.

### 3. Configure the request

Replace the placeholders with your own values:

| Placeholder | Replace with |
| --- | --- |
| `MINHA_INSTANCE` | Your Z-API instance ID |
| `MEU_TOKEN` | Your Z-API instance token |
| Sample phone numbers | Your intended recipient or test number |
| Sample payload values | Your message, media, or other request data |

Check the [current documentation](https://developer.z-api.io) and add any required authentication headers before running the request.

### 4. Review and run

Some snippets disable TLS certificate verification. Remove those overrides and keep certificate verification enabled.

Once you have reviewed the endpoint, credentials, and payload, run your file:

```bash
php example.php
```

Inspect the response and compare it with the current endpoint documentation.

## Compatibility Notes

This collection contains historical examples and testing notes. Request fields, authentication requirements, response formats, and HTTP status codes may have changed.

Some media payloads are shortened for illustration and must be replaced with complete values.

Use the examples as a reference, and consult the documentation when adapting them.

## Contributing

Found an outdated example or an opportunity to improve clarity? Open an issue or submit a pull request with the endpoint and proposed change.

Use placeholders for credentials and personal data in all contributions.

## Resources

- [Z-API Documentation](https://developer.z-api.io)
- [Z-API Website](https://z-api.io)
- [PHP cURL Documentation](https://www.php.net/manual/en/book.curl.php)

## License

This repository is licensed under the GNU General Public License v3.0. See [LICENSE](./LICENSE) for details.
