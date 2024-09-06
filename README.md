# Library Database Schema

This document outlines the normalized schema for a library database system.

## Schema Overview

### CARD
- **Number** (Primary Key)
- Fines
- Status

### CUSTOMER
- **ID** (Primary Key)
- Name
- Address
- Phone_number
- **Card_number** (Foreign Key referencing CARD(Number))
- Password
- User_name
- Date_sign_up

### EMPLOYEE
- **ID** (Primary Key)
- Name
- Address
- Phone_number
- **Card_number** (Foreign Key referencing CARD(Number))
- Password
- User_name
- Paycheck
- **Branch_name** (Foreign Key referencing BRANCH(Name))

### BRANCH
- **Name** (Primary Key)
- **Address** (Foreign Key referencing LOCATION(Address))
- Phone_number

### LOCATION
- **Address** (Primary Key)

### RENT
- **Card_ID** (Foreign Key referencing CARD(Number))
- **Item_ID** (Foreign Key referencing BOOK(ID) or VIDEO(ID))
- Date
- Return_date
- (Composite Primary Key: Card_ID, Item_ID, Date)

### BOOK
- **ISBN** (Primary Key)
- **ID** (Secondary Key, potentially unique if ISBN is not unique)
- State
- Availability
- Deby_cost
- Lost_cost
- **Address** (Foreign Key referencing LOCATION(Address))

### VIDEO
- **Title** (Primary Key, if titles are unique; otherwise, use a unique ID)
- **Year** (Part of Primary Key if Title is not unique)
- **ID** (Secondary Key, if Title-Year combination is not unique)
- State
- Availability
- Deby_cost
- Lost_cost
- **Address** (Foreign Key referencing LOCATION(Address))

## Notes
- Ensure that the **Item_ID** in the RENT table can reference either a BOOK or VIDEO. Depending on your SQL database capabilities, you might need to manage this with additional constraints or through application logic.
- In the BOOK and VIDEO tables, consider whether a composite key or a single unique identifier might be more appropriate.
- The LOCATION table is kept simple with just the Address, assuming addresses are unique. Adjust according to real-world requirements.

## Contributing
Feel free to fork this repository and contribute by submitting issues or pull requests.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
