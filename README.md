## Mini Venmo

Imagine that your phone and wallet are trying to have a beautiful baby. In order to make this happen, you must write a social payment app.  Implement a program that will feature users, credit cards, and payment feeds.

Requirements:

** input commands must be handled, passed with space delimited arguments, via stdin or a file passed on the command line

1. “user” will create a new user with a given name.
a) e.g., `user <user>`
b) User names should be alphanumeric but also allow underscores and dashes.
c) User names should be no shorter than 4 characters but no longer than 15.
d) Users start with a balance of $0.

2. “add” will create a new credit card for a given name, card number
a) e.g., `add <user> <card_number>`
b) Card numbers should be validated using Luhn-10.
c) Cards that fail Luhn-10 will display an error.
d) Cards that have already been added will display an error.

3. “pay” will create a payment between two users.
a) e.g., `pay <actor> <target> <amount> <note>`
b) <actor> and <target> are user names that were created in #1
c) Payments will always charge the actor's credit card (not decrement their balance).
d) Payments will always increase the target's balance.
e) If the actor user has no credit card, display an error.

4. “feed” will display a feed of the respective user’s payments.
a) e.g., `feed <user>`

5. “balance” will display a user’s balance
a) e.g. `balance <user>`

Input Assumptions:
* All input will be space delimited.
* Credit card numbers may vary in length, up to 19 characters.
* Credit card numbers will always be numeric.
* Amounts will be prefixed with “$” and will be dollars and cents

Example Input/Output:
> user Thomas
> user Lisa
> user Quincy
> add Thomas 4111111111111111
> add Lisa 5454545454545454
> add Quincy 1234567890123456
ERROR: This card is invalid
> pay Thomas Lisa $10.25 burritos
> pay Thomas Quincy $10.00 you’re awesome
> pay Lisa Quincy $5.00 pot-luck supplies
> pay Quincy Thomas $2.00 a subway card
ERROR: This user does not have a credit card.

> add Quincy 5454545454545454
ERROR: That card has already been added by another user, reported for fraud!
> add Quincy 5555555555554444

> pay Quincy Thomas $14.50 a redbull vodka
> feed Quincy
-- Thomas paid you $10.00 for you're awesome.
-- Lisa paid you $5.00 for pot-luck supplies.
-- You paid Thomas $14.50 for a redbull vodka.
> balance Quincy
-- $15.00
> feed Thomas
-- You paid Lisa $10.25 for burritos.
-- You paid Quincy $10.00 for you're awesome.
-- Quincy paid you $14.50 for a redbull vodka.
> feed Lisa
-- Thomas paid you $10.25 for burritos.
-- You paid Quincy $5.00 for pot-luck supplies.
