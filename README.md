# AI Teaching Assistant (AITA) Development Guide

This repository provides an overview of how the AI Teaching Assistant (AITA) was developed to automate the creation and posting of weekly course announcements in the Canvas LMS using Microsoft Power Automate, OpenAI's GPT-4, and other technologies.

## Overview

The AI Teaching Assistant (AITA) aims to enhance student engagement and instructor presence in online courses. It automates the creation of weekly announcements that include details about upcoming assignments and due dates, allowing instructors to focus more on teaching and interacting with students.

### Key Technologies Used

- **Microsoft Power Automate**: Used to create workflows for automating the extraction of assignment data from Canvas LMS, generating announcements using OpenAI's GPT-4, and posting these announcements to Canvas.
- **OpenAI's GPT-4**: Provides natural language processing capabilities to generate announcements based on extracted course data.
- **Canvas LMS**: The learning management system where course announcements are posted.
- **Qualtrics**: Provides a unique URL to share announcements and collect responses.
- **SharePoint**: Stores announcement data and collects responses from faculty members.

## Workflow

The AITA was developed using a three-part process in Power Automate:

### Part 1: Extract Assignments from Canvas LMS

- Scheduled to run every Monday at 7:45 AM.
- Utilizes a custom connector to the Canvas LMS instance to retrieve upcoming assignments and due dates for each course.
- Outputs the retrieved data in a structured format for further processing.

### Part 2: Create the Announcement

- Converts the extracted assignment data from CSV to HTML format using OpenAI's GPT-4.
- Groups assignments by type (e.g., Discussions, Assignments, Quizzes).
- Incorporates the course name, course code, assignment details (name, type, description, points, and due date), and links to each assignment on Canvas LMS.
- Stores the generated announcement in SharePoint with a unique ID for each course and week.

#### GPT Instructions

- The AI Teaching Assistant generates announcements using a predefined prompt:
  - Encourages students (referred to as "Tarleton Texans") at the beginning of the announcement.
  - Lists assignments with essential details like name, type, due date, and direct links to Canvas content.
  - Uses a supportive and motivational tone to engage students.
  - Ensures HTML code is correctly generated for Canvas LMS.

### Part 3: Log Acceptance or Approval

- Sends an email with a unique Qualtrics link to the course instructor.
- Instructors review the generated announcement, approving or rejecting it through the Qualtrics form.
- Logs the acceptance or rejection, including the instructor's comments, back to a SharePoint list for record-keeping and further analysis.

## Security and Privacy

- Ensures that only faculty members can approve announcements by implementing a security check.
- No sensitive student data is accessed or stored by the AITA.
- Maintains instructor and course data confidentiality through secure connections and data storage practices.

## Usage

To recreate this study and implement the AITA, you will need access to the following:

1. **Microsoft Power Automate**: For building and running automated workflows.
2. **Canvas LMS**: Access to the Canvas API for retrieving course assignments and posting announcements.
3. **OpenAI API (GPT-4)**: For generating the content of the announcements.
4. **Qualtrics**: For creating unique URLs and forms for faculty approval.
5. **Microsoft SharePoint**: For storing generated announcements and logging approval data.

### Steps to Implement

1. **Set up Power Automate Flows**:
   - Create custom connectors for Canvas and OpenAI API.
   - Develop three flows in Power Automate as described in the workflow above.

2. **Configure Canvas LMS**:
   - Enable API access and create a custom connector in Power Automate to interact with Canvas.

3. **Integrate OpenAI**:
   - Use the OpenAI GPT-4 model for generating announcements by passing the assignment data through a custom prompt.

4. **Set Up SharePoint Lists**:
   - Create lists in SharePoint to store the generated announcements and faculty approval data.

5. **Qualtrics Integration**:
   - Create a form to collect faculty approvals and link it to the SharePoint list.

## Additional Documentation

For more detailed information about specific aspects of the AI Teaching Assistant (AITA), please refer to the following documents:

### [AITA PROMPT](/AITA%20PROMPT.md)
This document contains the exact prompt used by the AI Teaching Assistant to generate weekly announcements. It provides insight into how the AI was instructed to format and structure the announcements, ensuring clarity and engagement for students.

### [DATA MANAGEMENT](/DATA%20MANAGEMENT.md)
An in-depth overview of how data is managed within the AITA system using SharePoint. This section describes the setup and use of SharePoint lists for storing announcements and tracking faculty approvals, detailing the fields used and how they integrate with Power Automate.

### [REQUIREMENTS](/REQUIREMENTS.md)
A comprehensive breakdown of the technical requirements and configurations needed to implement the AITA system. This document dives into the prerequisites, including account setups, software requirements, and detailed instructions for integrating the various components like Power Automate, OpenAI, Canvas LMS, Qualtrics, and SharePoint.


## Conclusion

The AITA streamlines the process of generating and posting weekly announcements in online courses, contributing to enhanced instructor presence and student engagement. This project leverages Microsoft Power Automate, OpenAI's GPT-4, Canvas LMS, Qualtrics, and SharePoint to provide an efficient and scalable solution.
