# Bank System Management

A simple command-line banking system in Python, built with object-oriented design. Customers can manage accounts, move money and take loans; admins can manage customers, apply interest and charge overdue loans. Data is saved between runs with `pickle`.

> Forked from [PwnWorld/bank-system-management](https://github.com/PwnWorld/bank-system-management).

![Screenshot](http://s4.picofile.com/file/8362954250/Screenshot_from_2019_06_08_14_38_05.png)

## Features

**Customers**
- Log in with name and password
- Deposit, withdraw (PIN-protected) and check balance
- Transfer money to other customers
- Request a loan of up to $10,000 (approved at random with a 30% chance)
- View and repay loans — each loan is due 30 days after it is issued
- Update profile (name, password, address)

**Admins**
- Run account operations and profile settings for any customer
- Delete customers (with a confirmation dialog)
- Print details of all customers and all admins
- Charge overdue loans
- Apply daily interest to every account

## Account types

| Class | Type | Interest rate | Notes |
|---|---|---|---|
| `hesabjari` | Current account | 4% | Default account |
| `hesabboland` | Savings (long-term) | 6% | Higher interest for saving |
| `hesabkotah` | Student (short-term) | 4% | Starts with a $100 bonus |

## Getting started

Requires Python 3 with `tkinter` (included in most Python installs; used for the yes/no confirmation dialogs).

```bash
git clone https://github.com/Nzzznin/bank-system-management.git
cd bank-system-management
python bank_system.py
```

The program seeds sample data on start-up, so you can log in right away:

| Role | Name | Password |
|---|---|---|
| Admin | `ahora` | `1441` |
| Customer | `amin` | `1234` |
| Customer | `Niloo` | `moonlight` |

Bank data is written to `bankData.pkl` in the working directory.

## Project structure

```
bank-system-management/
├── bank_system.py   # Entry point: BankSystem, menus, login, save/load
├── person.py        # Person, Customer and Admin classes
├── account.py       # Account base class and the three account types
└── loan.py          # Loan class: due date, repayment, report
```

## Class overview

```
Person ──┬── Customer   (owns Accounts)
         └── Admin      (full or limited rights)

Account ──┬── hesabjari ── hesabkotah
          └── hesabboland

Loan       (linked to an Account)
```
