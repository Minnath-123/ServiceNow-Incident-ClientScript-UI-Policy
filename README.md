# ServiceNow – Implement Client Script & UI Policy (Incident)

## 📌 Project Overview

The **Implement Client Script & UI Policy (Incident)** project demonstrates how ServiceNow client-side controls can be used to enforce data integrity and improve the usability of Incident records.

This project focuses on implementing **Client Scripts** and **UI Policies** on the ServiceNow **Incident** table. These configurations dynamically control form behavior based on user input and predefined conditions.

The implementation demonstrates how fields can be:

* Made mandatory based on specific conditions
* Automatically populated with values
* Displayed or hidden dynamically
* Enabled or disabled based on conditions
* Validated before record submission
* Controlled to ensure complete and valid Incident records

The overall objective is to ensure that Incident records contain the required information before they are submitted, while also providing a better and more controlled user experience.

---

## 🎯 Project Objective

The primary objective of this project is to demonstrate the practical implementation of **Client Scripts** and **UI Policies** in ServiceNow Incident Management.

The project aims to:

1. Enforce data integrity on Incident records.
2. Dynamically control Incident form fields.
3. Make specific fields mandatory when required.
4. Automatically populate field values based on conditions.
5. Control field visibility and accessibility.
6. Validate user-entered information before submission.
7. Prevent incomplete Incident records from being submitted.
8. Improve consistency in Incident data.
9. Provide a better user experience for ServiceNow users.
10. Demonstrate practical ServiceNow configuration skills.

---

## 🏢 Platform Used

| Component                 | Technology            |
| ------------------------- | --------------------- |
| Platform                  | ServiceNow            |
| Application               | Incident Management   |
| Table                     | Incident `[incident]` |
| Client-side Configuration | Client Scripts        |
| Form Configuration        | UI Policies           |
| Scripting Language        | JavaScript            |
| Interface                 | ServiceNow Web UI     |
| Development Environment   | ServiceNow Instance   |

---

## 🧩 Key Concepts

### 1. Client Script

A **Client Script** is a JavaScript-based ServiceNow configuration that runs on the client side, generally within the user's browser.

Client Scripts are commonly used to:

* Validate user input
* Set field values
* Clear field values
* Display messages
* Make fields mandatory
* Control form behavior
* Prevent form submission
* Respond to field changes

Client Scripts can run during different form events.

Common Client Script types include:

* `onLoad`
* `onChange`
* `onSubmit`
* `onCellEdit`

---

### 2. UI Policy

A **UI Policy** is a ServiceNow configuration used to dynamically control form fields without requiring extensive scripting.

UI Policies can be used to:

* Make fields mandatory
* Make fields visible or hidden
* Make fields read-only
* Change field behavior based on conditions

UI Policies are particularly useful when the required behavior can be achieved using configuration rather than JavaScript.

---

## 🏗️ Project Architecture

The project follows a client-side form control approach:

```text
                    ServiceNow Instance
                           |
                           v
                    Incident Form
                           |
             +-------------+-------------+
             |                           |
             v                           v
        UI Policies                Client Scripts
             |                           |
             v                           v
      Field Behaviour             Dynamic Logic
             |                           |
             +-------------+-------------+
                           |
                           v
                 Incident Validation
                           |
                           v
                  Valid Incident Record
```

---

# ⚙️ Project Implementation

## 1. Incident Form

The project is implemented on the **Incident** table.

The Incident form contains commonly used fields such as:

* Number
* Caller
* Category
* Subcategory
* Service
* Configuration Item
* Impact
* Urgency
* Priority
* Assignment Group
* Assigned To
* Short Description
* Description
* State
* Resolution Information

The Client Scripts and UI Policies are configured to control the behavior of selected fields.

---

# 🔹 UI Policy Implementation

## Purpose

The UI Policy is used to dynamically control Incident form fields according to predefined conditions.

For example, when a particular condition becomes true, the UI Policy can automatically make a field mandatory.

### Example Scenario

If the Incident requires additional information based on a selected condition, the corresponding field can be made mandatory automatically.

### UI Policy Configuration

Typical configuration includes:

```text
Table:
Incident [incident]

Active:
Yes

Condition:
Defined based on Incident field values

Reverse if False:
Enabled when required
```

### UI Policy Actions

The UI Policy Action can control:

```text
Mandatory
Visible
Read-only
```

This allows the form to react dynamically without requiring the user to manually configure each field.

---

# 🔹 Client Script Implementation

Client Scripts are used when more advanced client-side logic is required.

The project demonstrates the use of Client Scripts for:

* Automatic field population
* Dynamic field behavior
* Form validation
* Submission control
* User notifications

---

## 📌 OnLoad Client Script

An **onLoad Client Script** executes when the Incident form is loaded.

### Purpose

It can be used to:

* Initialize form fields
* Set default values
* Display informational messages
* Configure initial field behavior

### Execution Flow

```text
User opens Incident form
          |
          v
onLoad Client Script executes
          |
          v
Initial form conditions are checked
          |
          v
Required field behavior is applied
```

---

# 📌 OnChange Client Script

An **onChange Client Script** executes whenever the value of a specified field changes.

### Purpose

It is useful for dynamic form behavior.

For example:

```text
User changes Category
        |
        v
onChange Client Script executes
        |
        v
Condition is evaluated
        |
        v
Related field is updated
```

This provides a dynamic and responsive Incident form.

---

# 📌 OnSubmit Client Script

An **onSubmit Client Script** executes when the user attempts to submit the Incident form.

### Purpose

The main purpose is to validate the form before the record is submitted.

The script checks whether required information has been provided.

### Validation Flow

```text
User clicks Submit
        |
        v
onSubmit Client Script executes
        |
        v
Required information checked
        |
     +--+--+
     |     |
   Valid  Invalid
     |     |
     v     v
 Submit   Stop submission
 record   + display message
```

If the required information is missing, the submission can be prevented until the user provides valid information.

---

# 🔐 Data Validation

Data validation is one of the main objectives of this project.

The implementation ensures that users cannot easily create incomplete Incident records.

### Validation Process

```text
Incident Form
     |
     v
User enters information
     |
     v
Client-side validation
     |
     +----------------+
     |                |
     v                v
Valid Data       Missing Data
     |                |
     v                v
Allow Submit     Prevent Submit
     |                |
     v                v
Incident Created  Display Message
```

This helps maintain data quality across the Incident table.

---

# 🎯 Functional Requirements

The project includes the following functional requirements:

### FR-01: Dynamic Mandatory Fields

The system should dynamically make selected Incident fields mandatory based on configured conditions.

### FR-02: Dynamic Field Behaviour

The system should change field behavior according to user input and form conditions.

### FR-03: Automatic Field Population

The Client Script should be capable of automatically setting field values when the defined condition is satisfied.

### FR-04: Form Validation

The system should validate required information before allowing the Incident record to be submitted.

### FR-05: Submission Control

If required information is missing, the system should prevent the Incident from being submitted.

### FR-06: User Feedback

The system should provide appropriate messages to help users understand missing or invalid information.

---

# 🧪 Testing

Testing is performed to verify that the configured Client Scripts and UI Policies work correctly.

## Test Case 1 – Incident Form Loading

**Objective:** Verify that the form loads correctly.

**Steps:**

1. Open the Incident module.
2. Create a new Incident.
3. Observe the form.
4. Verify the initial field behavior.

**Expected Result:**

The Incident form should load successfully and the configured client-side behavior should be applied.

---

## Test Case 2 – UI Policy Condition

**Objective:** Verify dynamic field behavior.

**Steps:**

1. Open a new Incident.
2. Enter the required values.
3. Trigger the configured UI Policy condition.
4. Observe the affected field.

**Expected Result:**

The configured field behavior should change according to the UI Policy.

---

## Test Case 3 – Client Script Execution

**Objective:** Verify that the Client Script executes correctly.

**Steps:**

1. Open an Incident form.
2. Change the configured field.
3. Observe the form behavior.
4. Verify the expected action.

**Expected Result:**

The Client Script should execute and apply the configured logic.

---

## Test Case 4 – Mandatory Field Validation

**Objective:** Verify mandatory field enforcement.

**Steps:**

1. Open a new Incident.
2. Leave the configured required field empty.
3. Click Submit.

**Expected Result:**

The system should prevent submission when the required information is missing.

---

## Test Case 5 – Successful Submission

**Objective:** Verify that a valid Incident can be submitted.

**Steps:**

1. Open a new Incident.
2. Enter all required information.
3. Complete the required fields.
4. Click Submit.

**Expected Result:**

The Incident should be successfully created.

---

# 📊 Test Result Summary

| Test Case | Scenario                  | Expected Result             | Status |
| --------- | ------------------------- | --------------------------- | ------ |
| TC-01     | Incident form loading     | Form loads correctly        | Passed |
| TC-02     | UI Policy condition       | Field behavior changes      | Passed |
| TC-03     | Client Script execution   | Script executes correctly   | Passed |
| TC-04     | Missing required data     | Submission prevented        | Passed |
| TC-05     | Valid Incident submission | Record created successfully | Passed |

---

# 🛡️ Data Integrity

Data integrity is a major focus of this implementation.

Without proper validation, users may create Incident records containing:

* Missing information
* Incorrect values
* Incomplete descriptions
* Inconsistent field data

The combination of UI Policies and Client Scripts helps reduce these problems.

### Benefits

* Better data quality
* Consistent Incident records
* Reduced incomplete submissions
* Improved user experience
* Better reporting accuracy
* Improved Incident management

---

# 🔄 Overall Project Workflow

```text
                    START
                      |
                      v
             Open Incident Form
                      |
                      v
             Form Loads Successfully
                      |
                      v
               UI Policies Run
                      |
                      v
             Client Scripts Run
                      |
                      v
             User Enters Data
                      |
                      v
              Field Value Changes
                      |
                      v
             Dynamic Validation
                      |
                      v
              User Clicks Submit
                      |
                      v
              onSubmit Validation
                      |
                +-----+-----+
                |           |
              Valid       Invalid
                |           |
                v           v
        Incident Created   Submission
                           Prevented
                              |
                              v
                        Error/Message
                              |
                              v
                         Correct Data
                              |
                              v
                           Submit
```

---

# 📁 Suggested GitHub Repository Structure

```text
serviceNow-client-script-ui-policy/
│
├── README.md
│
├── client-scripts/
│   ├── onLoad/
│   ├── onChange/
│   └── onSubmit/
│
├── ui-policies/
│   ├── ui-policy-configuration.md
│   └── ui-policy-actions.md
│
├── screenshots/
│   ├── incident-form.png
│   ├── client-script.png
│   ├── ui-policy.png
│   ├── ui-policy-action.png
│   ├── validation.png
│   └── final-output.png
│
└── documentation/
    └── implementation-details.md
```

> The exact folder structure can be adjusted depending on how you organize your ServiceNow project screenshots and documentation.

---

# 🖥️ Screenshots

Screenshots can be added to the repository to demonstrate the implementation.

Recommended screenshots:

### 1. Incident Form

```text
screenshots/incident-form.png
```

Shows the Incident form used for the implementation.

### 2. Client Script Configuration

```text
screenshots/client-script.png
```

Shows the Client Script configuration.

### 3. UI Policy Configuration

```text
screenshots/ui-policy.png
```

Shows the configured UI Policy.

### 4. UI Policy Action

```text
screenshots/ui-policy-action.png
```

Shows the fields controlled by the UI Policy.

### 5. Validation Message

```text
screenshots/validation.png
```

Shows the validation behavior when required information is missing.

### 6. Final Incident Record

```text
screenshots/final-output.png
```

Shows the successfully created Incident record.

---

# 📚 ServiceNow Features Used

This project uses the following ServiceNow features:

* Incident Management
* Incident Table
* Client Scripts
* UI Policies
* UI Policy Actions
* JavaScript
* Form Validation
* Dynamic Form Behaviour
* Client-side Data Validation

---

# 💡 Why Client Scripts and UI Policies?

Client Scripts and UI Policies are important ServiceNow configuration tools because they allow administrators and developers to create dynamic and user-friendly forms.

### UI Policies

UI Policies are suitable for straightforward field behavior such as:

```text
Mandatory
Visible
Read-only
```

### Client Scripts

Client Scripts are suitable for more complex requirements such as:

```text
Conditional logic
Automatic value assignment
Custom validation
User messages
Submission control
Dynamic processing
```

Using both features together provides a flexible approach for controlling Incident forms.

---

# 🚀 Benefits of the Project

The implementation provides several benefits.

## 1. Improved Data Quality

Required information is enforced before an Incident can be submitted.

## 2. Better User Experience

Users receive dynamic feedback based on their actions.

## 3. Reduced Manual Errors

Automatic field behavior reduces unnecessary manual data entry.

## 4. Consistent Records

Incident records follow the configured data requirements.

## 5. Better Incident Management

Complete and consistent Incident information supports better Incident tracking and management.

## 6. Practical ServiceNow Experience

The project demonstrates practical knowledge of ServiceNow configuration and JavaScript-based client-side development.

---

# 🔮 Future Enhancements

The project can be extended with additional ServiceNow functionality.

Possible enhancements include:

* Advanced Incident validation
* Script Includes
* Business Rules
* Data Policies
* UI Actions
* Client-side notifications
* Automated Incident assignment
* Automatic priority calculation
* SLA integration
* Email notifications
* Flow Designer automation
* Incident categorization
* Duplicate Incident detection
* Role-based form behavior
* Advanced reporting and dashboards

---

# 🎓 Learning Outcomes

After completing this project, the developer gains practical understanding of:

* ServiceNow Incident Management
* Incident table configuration
* Client Scripts
* UI Policies
* UI Policy Actions
* JavaScript in ServiceNow
* Client-side validation
* Dynamic form behavior
* Mandatory field control
* Form submission validation
* Data integrity concepts
* ServiceNow development practices

---

# 📌 Project Highlights

```text
✓ ServiceNow Incident Management
✓ Client Script Implementation
✓ UI Policy Implementation
✓ Dynamic Form Behaviour
✓ Mandatory Field Control
✓ Automatic Field Population
✓ Client-side Validation
✓ Submission Control
✓ Data Integrity Enforcement
✓ User Feedback
✓ Incident Form Customization
```

---

# 📝 Conclusion

The **Implement Client Script & UI Policy (Incident)** project demonstrates how ServiceNow client-side configurations can be used to improve the quality, consistency, and usability of Incident records.

By combining **UI Policies** and **Client Scripts**, the Incident form can dynamically respond to user input, enforce mandatory information, populate fields when required, validate submitted data, and prevent incomplete records from being created.

The implementation provides a practical demonstration of ServiceNow development concepts and shows how client-side controls can be applied to real-world Incident Management requirements.

Overall, the project establishes a strong foundation for further ServiceNow development using **Client Scripts, UI Policies, Business Rules, Script Includes, UI Actions, Flow Designer, and other platform capabilities**.

---

# 👩‍💻 Author

**Project:** Implement Client Script & UI Policy (Incident)

**Platform:** ServiceNow

**Domain:** IT Service Management (ITSM)

**Module:** Incident Management

**Technology:** ServiceNow + JavaScript

---

# 📄 License

This project is created for **educational and learning purposes** to demonstrate ServiceNow Incident Management, Client Scripts, and UI Policies.
