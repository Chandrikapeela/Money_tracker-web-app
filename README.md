# Money_tracker-web-app
# Expense Tracker

## Overview

The Expense Tracker is a simple web application designed to help users keep track of their expenses. It allows users to add expenses, view them in a table, and see the total amount spent. The application provides a clean and straightforward interface for expense management.

## Features

- **Add Expenses**: Input the name and amount of the expense and add it to the list.
- **View Expenses**: Display a list of added expenses in a table format.
- **Remove Expenses**: Remove individual expenses from the list.
- **Total Amount**: View the total amount of all expenses.

## Installation

To set up and run the Expense Tracker application, follow these steps:

1. **Download or Clone the Repository**

   Download the source code as a ZIP file or clone the repository using Git:
   ```bash
   git clone https://github.com/yourusername/expense-tracker.git
   ```

2. **Navigate to the Project Directory**

   Change to the project directory:
   ```bash
   cd expense-tracker
   ```

3. **Set Up Dependencies**

   There are no external dependencies for this project. It uses standard HTML, CSS, and JavaScript.

4. **Open the Application**

   Open the `index.html` file in a web browser to view and use the application:
   ```bash
   open index.html
   ```

## Usage

1. **Add an Expense**:
   - Enter the name of the expense in the "Expense Name" field.
   - Enter the amount in the "Amount" field.
   - Click the "Add Expense" button to add the expense to the list.

2. **View and Manage Expenses**:
   - The added expenses will be displayed in a table.
   - You can remove an expense by clicking the corresponding "Delete" button in the table.

3. **View Total Amount**:
   - The total amount of all added expenses will be displayed at the bottom of the table.

## Code Explanation

- **HTML**: Defines the structure of the Expense Tracker application.
  - `form` for adding new expenses.
  - `input` fields for expense name and amount.
  - `button` to submit the form and add expenses.
  - `table` to display the list of expenses.
  - `div` for showing the total amount.

- **CSS**: (In `style.css`) Used for styling the user interface. Customize this file to change the appearance of the application.

- **JavaScript**: (In `script.js`) Handles the functionality of adding expenses, removing them, and updating the total amount.

Here’s a brief example of how the JavaScript might look in `script.js`:

```javascript
document.getElementById('expense-form').addEventListener('submit', function(event) {
    event.preventDefault();
    
    const name = document.getElementById('expense-name').value;
    const amount = parseFloat(document.getElementById('expense-amount').value);
    
    if (name && !isNaN(amount)) {
        addExpense(name, amount);
        updateTotal();
        document.getElementById('expense-name').value = '';
        document.getElementById('expense-amount').value = '';
    }
});

function addExpense(name, amount) {
    const tableBody = document.getElementById('expense-list');
    
    const row = document.createElement('tr');
    row.innerHTML = `
        <td>${name}</td>
        <td>${amount.toFixed(2)}</td>
        <td><button onclick="removeExpense(this)">Delete</button></td>
    `;
    
    tableBody.appendChild(row);
}

function removeExpense(button) {
    const row = button.parentElement.parentElement;
    row.remove();
    updateTotal();
}

function updateTotal() {
    const rows = document.querySelectorAll('#expense-list tr');
    let total = 0;
    
    rows.forEach(row => {
        const amount = parseFloat(row.cells[1].innerText);
        total += amount;
    });
    
    document.getElementById('total-amount').innerText = total.toFixed(2);
}
```

## Contributing

Contributions are welcome! If you have suggestions or improvements, please fork the repository and create a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For any inquiries or issues, please contact peelachandrika@gmail.com

---

