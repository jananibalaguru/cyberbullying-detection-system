# Cyberbullying Detection System

A Flask-based social media cyberbullying detection application for analyzing tweets, visualizing cyberbullying categories, and providing user and administrator interfaces.

## Project Overview

The system loads a labeled tweet dataset, cleans and prepares the text, analyzes category-specific words, trains or evaluates text classification approaches, and presents results through a web interface. It also includes user registration, login, posting, profile management, and administrator views.

## Features

- User registration and login
- Administrator login and dashboard
- Social-media-style text and image posts
- Cyberbullying keyword detection
- Tweet text preprocessing
- Category-specific word-frequency analysis
- Cyberbullying visualization dashboards
- Train/test dataset splitting
- Classification result pages
- MySQL-backed user and post data

## Cyberbullying Categories

The main dataset includes the following categories:

- Not cyberbullying
- Gender
- Religion
- Other cyberbullying
- Age
- Ethnicity

## Project Workflow

1. Load `cyberbullying_tweets.csv` through the Flask application.
2. Inspect the source tweet text and assigned cyberbullying category.
3. Lowercase tweet text.
4. Remove hashtags, URLs, mentions, usernames, symbols, and non-alphanumeric characters.
5. Remove stopwords, including additional social-media-specific terms.
6. Apply Porter stemming to normalize words.
7. Store cleaned text in a new `tweet_clean` field.
8. Split cleaned text into word lists.
9. Count and rank the most frequent words overall.
10. Analyze frequent words separately for each cyberbullying category.
11. Display category and word-frequency information in application pages.
12. Map category names to numeric labels.
13. Split records into training and testing sets using a 33 percent test size.
14. Apply text and classification components for cyberbullying detection.
15. Allow users to submit posts and images.
16. Check submitted text against configured negative keywords.
17. Store approved and flagged post information in MySQL.
18. Provide classification summaries and visual charts for review.
19. Let administrators view registered users and application activity.

## Project Structure

```text
cyber_bullying/
|-- main.py                 Flask application and routes
|-- database/
|   `-- cyber_bullying.sql  MySQL database schema and sample data
|-- dataset/
|   |-- cyberbullying_tweets.csv
|   `-- data.csv
|-- static/
|   |-- css/
|   |-- comments/
|   |-- graph/
|   |-- images/
|   `-- vendors/
|-- templates/
|   `-- HTML application pages
|-- requirements.txt
`-- README.md
```

## Requirements

- Python 3.7 or a compatible Python 3 environment
- WampServer or another MySQL and Apache setup
- MySQL database named `cyber_bullying`
- Modern web browser

## Installation

1. Clone this repository.
2. Open a terminal in the project directory.
3. Create and activate a virtual environment:

```bash
python -m venv venv
venv\Scripts\activate
```

4. Install dependencies:

```bash
pip install -r requirements.txt
```

5. Start WampServer or MySQL.
6. Import `database/cyber_bullying.sql` into phpMyAdmin or the MySQL command line.
7. Confirm the database settings in `main.py`:

```text
host: localhost
user: root
password: (empty by default)
database: cyber_bullying
```

Update these values if the local MySQL credentials differ.

8. Run the Flask application:

```bash
python main.py
```

9. Open the application URL reported by Flask in a browser.

## Database Setup

Import the SQL file using phpMyAdmin:

1. Open `http://localhost/phpmyadmin`.
2. Create a database named `cyber_bullying`.
3. Select the database.
4. Open the Import tab.
5. Choose `database/cyber_bullying.sql`.
6. Run the import.

## Sample Credentials

The SQL import includes sample records. Change default passwords before deploying the application to a public or shared environment.

## Data

- `dataset/cyberbullying_tweets.csv`: labeled tweets and cyberbullying categories
- `dataset/data.csv`: secondary cleaned tweet data

## Security Note

This project is a college/demo application and is not production-ready. Before deployment, the following should be improved:

- Password hashing
- Environment-based database credentials
- Strong Flask secret management
- SQL query parameter validation
- Secure session configuration
- File upload validation
- CSRF protection
- Debug-mode restrictions
