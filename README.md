Rule Engine with AST

# Objective:

This repository contains a 3-tier rule engine application that evaluates user eligibility based on attributes like age, department, income, spend, etc. The system uses an Abstract Syntax Tree (AST) to represent and manage conditional rules, allowing dynamic creation, combination, and modification of these rules.

# Features:

1. Create, combine, and modify rules using AST.
2. Dynamic rule evaluation based on attributes.
3. MongoDB is used for data storage.
4. Simple API and frontend interface to manage rules.

# Data Structure:
The AST is represented using a node-based structure:

Node Structure:
type: A string indicating the node type (operator for AND/OR, operand for conditions).
left: Reference to the left child node.
right: Reference to the right child node.
value: The actual condition (e.g., age > 30) for operand nodes.

Data Storage
MongoDB is used to store the rules and metadata.
A rule is saved in both string format and as an AST.

# Sample Data:

{
  "_id": { "$oid": "6711e33897e50c81ddb6ea6d" },
  "ruleString": "(age > 30 AND department = 'Sales') OR (age < 25 AND department = 'Marketing') AND (salary > 50000 OR experience > 5)",
  "ast": { /* Abstract Syntax Tree structure */ }
}

Sample Rules:

Rule 1: ((age > 30 AND department = 'Sales') OR (age < 25 AND department = 'Marketing')) AND (salary > 50000 OR experience > 5)

Rule 2: ((age > 30 AND department = 'Marketing')) AND (salary > 20000 OR experience > 5)

# API Design: 

1. create_rule(rule_string)
Input: Rule string (e.g., "age > 30 AND department = 'Sales'")
Output: AST representing the rule.
Description: Converts a rule string into an AST structure.
2. combine_rules(rules)
Input: List of rule strings.
Output: Combined AST.
Description: Combines multiple rules into a single AST efficiently, avoiding redundant checks.
3. evaluate_rule(JSON data)
Input: AST and a dictionary of attributes (e.g., {"age": 35, "department": "Sales", "salary": 60000, "experience": 3})
Output: Boolean (True if data satisfies the rule, False otherwise).
Description: Evaluates a rule against the provided attributes.

# Test Cases:

1.1 Creating Rules
Convert rules to AST using create_rule and verify their correctness.

1.2 Combining Rules
Combine multiple rules and check the combined AST for correctness.

1.3 Evaluating Rules
Provide sample JSON data and test the evaluate_rule function to ensure the rule logic works as expected.

# Bonus Features:

2.1 Error Handling
Handle invalid rule strings or incorrect data formats.

2.2 Attribute Validation
Ensure attributes are part of a pre-defined catalog.

2.3 Rule Modification
Allow existing rules to be modified using additional functions.

2.4 User-defined Functions
Optionally extend the system to support custom functions in the rule language.

# Project Structure:

Backend (Node.js)

Folder: rule-engine

Key Files:

1. src/: Contains controllers, models, and utility functions.
2. index.js: Main entry point for the backend.
3. .env: Environment variables for the backend.
4. package.json: Dependencies and scripts.
   
Frontend (React, Vite, Tailwind CSS)

Folder: rule-engine-frontend

Key Files:

1. src/: React components and logic.
2. tailwind.config.js: Tailwind CSS configuration.
3. vite.config.js: Vite configuration for the frontend.
4. .eslintrc.cjs: ESLint configuration.

# Installation and Setup:

Backend

1. Navigate to the rule-engine directory:
   
    cd rule-engine

3. Install the dependencies:
   
    npm install

4. Create a .env file and add necessary environment variables, including your database URL:
   
    HORA_DATABASE=<your_database_url>

5. Start the backend server:
   
    npm start

# Frontend:

1. Navigate to the rule-engine-frontend directory:
   
    cd rule-engine-frontend

2. Install the dependencies:
   
    npm install

3. Start the frontend development server:
   
    npm run dev

# Usage:

1. Open the frontend application in your browser.

2. Use the interface to create, combine, and evaluate rules dynamically.

3. The backend API will handle rule creation, combination, and evaluation based on the attributes you provide.
