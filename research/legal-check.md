How to Use Plaid Safely (Without Becoming a Transmitter)

If you still want to utilize Plaid on your platform, you must separate data collection from payment processing:

 - The "Pledge to Self" Tracking: You can safely use Plaid Auth to let a user securely log into their bank. Your website can track their balance or transactions internally to prove they are keeping their "pledge to self". Because no money leaves their bank via your website, you remain entirely exempt. 

 - The "Bring Your Own Processor" (BYOP) Strategy: If you want a user to donate, use Plaid to verify their bank information, but pass that data token over to a heavily regulated, fully licensed merchant aggregator like Stripe Connect or Braintree. In this model, the licensed partner serves as the legal transmitter on record, completely shielding your software layer from holding liability. 

Other Options

1. GoFundMe - "transfers money internally and to external banks by processing credit or debit card donations through third-party payment partners like Stripe or Adyen"

2. Venmo - "moves money internally between users instantly by adjusting digital ledger balances stored in its own system rather than moving physical cash or running a bank wire for each peer-to-peer payment"

3. Paypal - "ledger-based system that updates account balances instantly without moving physical cash between banks for on-platform transactions." 