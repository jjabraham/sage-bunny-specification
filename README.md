# SageBunny - Specification

This is a specification for a simple banking server. This is not even remotely production ready. The aim is to have a set of toy specifications for a domain that will allow a developer to test out basic functionality such as:

1. DB access (CRUD functionality)
2. Accessing external APIs
3. Unit testing

## Domain

The app should implement the following functionality:

1. Create an account
2. Delete an account
    * must have 0 balance
3. update account details
    * except balance - balance is updated only by transactions
4. Create customer
5. Delete customer
    * must have all accounts 0 balance
6. update customer details
7. Transaction -> **Withdraw** amount from account (debit)
    * amount supplied should be deducted from account balance
    * must fail if amount supplied is greater than balance
8. Transaction -> **Deposit** amount to account (credit)
    * account balance should be increased by the supplied amount
9. Transaction -> **Transfer** amount between accounts (debit + credit)
    * debit amount from source account
    * all normal debit rules apply
    * credit amount to target account
    * transaction should be atomic - the entire transfer transaction should fail and rollback if either the debit or credit fail

### Models

![Customer](/assets/images/model-customer.png)
![Account](/assets/images/model-account.png)
![Transaction](/assets/images/model-transaction.png)

## Application

1. App should validate domain objects before operating on them
2. Automated unit tests
3. Interfaces -  should be able to add aditional interfaces easily
    * REST
    * CLI