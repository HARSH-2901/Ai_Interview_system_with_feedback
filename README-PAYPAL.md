# PayPal Subscription Integration Guide

This document provides instructions on how to set up and configure the PayPal subscription integration for the application.

## Overview

The application uses the PayPal Subscription API to handle recurring payments. The integration follows these steps:

1. Client-side renders a PayPal subscription button using the PayPal JavaScript SDK
2. User completes the subscription process directly with PayPal
3. PayPal sends a webhook to our backend to confirm the subscription
4. Backend updates the user's subscription status

## Setup Requirements

### 1. PayPal Developer Account

1. Create a PayPal Developer account at [developer.paypal.com](https://developer.paypal.com)
2. Create a new REST API app in the Developer Dashboard
3. Get your Client ID and Secret from the app credentials

### 2. Create PayPal Subscription Plans

1. Log in to your PayPal Business account
2. Go to Products & Services > Subscriptions
3. Create subscription plans for each tier (Bronze, Gold, Diamond) with both monthly and yearly billing cycles
4. Note the Plan IDs for each created plan

### 3. Environment Variables

Set the following environment variables in your Supabase project:

```
PAYPAL_CLIENT_ID=your_client_id
PAYPAL_SECRET_KEY=your_secret_key
PAYPAL_API_URL=https://api-m.sandbox.paypal.com  # Use https://api-m.paypal.com for production

# Plan IDs
PAYPAL_BRONZE_MONTHLY_PLAN_ID=P-XXXXXXXXXXXXXXX
PAYPAL_GOLD_MONTHLY_PLAN_ID=P-XXXXXXXXXXXXXXX
PAYPAL_DIAMOND_MONTHLY_PLAN_ID=P-XXXXXXXXXXXXXXX
PAYPAL_BRONZE_YEARLY_PLAN_ID=P-XXXXXXXXXXXXXXX
PAYPAL_GOLD_YEARLY_PLAN_ID=P-XXXXXXXXXXXXXXX
PAYPAL_DIAMOND_YEARLY_PLAN_ID=P-XXXXXXXXXXXXXXX
```

### 4. PayPal SDK Configuration

The PayPal JavaScript SDK is loaded in the HTML file with the following configuration:

```html
<script src="https://www.paypal.com/sdk/js?client-id=your_client_id&vault=true&intent=subscription"></script>
```

Replace `your_client_id` with your actual PayPal Client ID. In development, you can use `test` as the client ID for testing.

For production, update the `index.html` file with your actual client ID:

```html
<script src="https://www.paypal.com/sdk/js?client-id=YOUR_PRODUCTION_CLIENT_ID&vault=true&intent=subscription"></script>
```

## Testing

### Sandbox Testing

1. Use the PayPal Sandbox environment for testing
2. Create Sandbox personal and business accounts in the PayPal Developer Dashboard
3. Use the Sandbox personal account to make test subscriptions

### Common Testing Issues

1. **Popup blocked**: Ensure popups are allowed for your development domain
2. **401 Unauthorized**: Check that your Client ID and Secret are correct
3. **400 Bad Request**: Verify that the plan IDs are correct and active
4. **Webhook not received**: Check your webhook URL configuration in the PayPal Developer Dashboard

## Troubleshooting

If you encounter issues with the PayPal integration:

1. Check the browser console for client-side errors
2. Check the Supabase Edge Function logs for server-side errors
3. Verify that all environment variables are set correctly
4. Ensure that the PayPal plans are active and configured correctly

## Implementation Details

### Client-Side Components

- `PayPalSubscriptionButton.tsx`: Renders the PayPal button and handles the subscription process
- `PaymentDialog.tsx`: Manages the payment dialog UI and subscription state

### Server-Side Functions

- `get-paypal-plan-id`: Edge Function that returns the appropriate plan ID based on the selected subscription tier
- `webhook-handler`: (Future implementation) Edge Function that processes PayPal webhooks to update the user's subscription status

## Additional Resources

- [PayPal Subscriptions API Documentation](https://developer.paypal.com/docs/subscriptions/)
- [PayPal JavaScript SDK Documentation](https://developer.paypal.com/docs/business/javascript-sdk/javascript-sdk-reference/)
- [PayPal Webhook Documentation](https://developer.paypal.com/api/rest/webhooks/) 