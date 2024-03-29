# Transaction and Payment Status

| Transaction Status | Individual Payment Status | Description|
| ------------------ | ------------------------- | ---------- |
| **TF** - Transaction Failed| **DF** – Disbursement Failed| Validation failed while processing request|
| **PA** - Pending Approval| **DP** - Disbursement Pending| Transaction accepted into the disbursement's platform but waiting on merchant approval workflow.|
| **PD** - Pending Disbursement| **DP** – Disbursement Pending| At this point this transaction is ready for recipient acceptance|
| **IP** - In Process| **DS** – Disbursement Selected| When at least one of the recipients has provided payment information|
| **IP** – In Process| **DA** – Disbursement Accepted| Payment status for secondary recipients once accepted|
| **IP** – In Process| **IP** – In Process| Only applied for Venmo/Paypal disbursement. This is due to async nature of Venmo/Paypal payout.|
| **TC** – Transaction Completed| **DR** – Disbursement Rejected| If Primary or secondary recipient declines the payment.|
| **TC** – Transaction Completed| **DI** – Disbursed| After all recipients have accepted. Primary recipient status is updated to Disbursed|
| **IP** - In Process| **DD**  - Disbursement Declined| Declined by downstream issuer|
| **TC** – Transaction Completed| **DH** – Disbursement Fraud Hold| Declined by Fiserv Fraud system|
| **TC** – Transaction Completed| **DA** – Disbursement Accepted| After all recipients have accepted. Secondary recipient status will remain Accepted|
| **TV** – Transaction Cancelled| **PC**- Payment Cancelled| Before the payment status moves to Disbursed, the merchant can cancel a payment. database will show this as **`CANCELLED`** |  
| **TC** – Transaction Completed| **AR** – In house Reversal| Merchant cancel the payment after the disbursement but NACHA file has not prepared. Fund is still at blue check. As of now this happens at 7:00PM ET. database will show this as **`INHOUSE_REVERSED`**"|
| **TC** – Transaction Completed| **RP** - Reversal Pending| Transactions for which refund is initiated after Disbursement. |
| **TR** – Transaction Reversed| **PC**- Payment Cancelled| database will still show this as **`DISBURSED`** |
| **TC** – Transaction Completed| **RS** – Reversal Success | Merchant cancel the payment|  after the disbursement and NACHA file has been send to the bank. ACH reversal status updated to success after 5 working days. This is the confirmation that no reversal failure notification came to DDP platform from bank."|
| **TV** – Transaction Cancelled| **PC**- Payment Cancelled| database will show this as **`REVERSED`** |
| **TC** – Transaction Completed| **RF** – Reversal Failed | ACH reversal after disbursement failed. |
| **TR**- Transaction Reversed| **ARF** – ACH Reversal failed | (Settlement/Reconciliation Scheduler)  database will show this as **`REJECTED`** |
| **TE** – Transaction Expired | **PE**- Payment Expired| If all recipients have not accepted payment within set number of days defined at a merchant level|
| **TC** – Transaction Completed | **DC** – Disbursement Charged back| For ACH Rejects/Issuer charge backs/ACH Returns<br>Cause: <ul><li>Wrong card number</li><li>ACH Account Closed</li><li>User returned the credit</li><ul> |
| **TC**- Transaction Completed | **AF** – Authentication Failed | Authentication failed after 3 retry (Phone#/OTP)|
| **TC**- Transaction Completed | **RE** – Retry Exceeded | Max retry count reached for payment/disbursement |
| **TV**- Transaction Cancelled | **DNF** – Delivery notification failed| Email/SMS delivery failed.(Failed Email Scheduler) |
