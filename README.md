# NSU Course Notifier Bot

The NSU Course Notifier Bot is a Telegram bot designed to help students at North South University (NSU) stay updated on course seat availability. The bot periodically scrapes the course data from the NSU website, saves it to an Excel file, and notifies users about seat availability based on their preferences.

## Features

- **Set Course Preferences**: Users can set their preferred course and section.
- **Check Seat Availability**: Users can check the current seat availability for their preferred course and section.
- **Automated Notifications**: The bot automatically notifies users when seats become available or if no seats are available within 30 minutes.

## How It Works

1. **Data Scraping**: The bot periodically scrapes course data from the NSU website and saves it to an Excel file.
2. **Excel File**: The scraped data is stored in an `course_data.xlsx` file.
3. **User Preferences**: Users set their course and section preferences using the bot commands.
4. **Periodic Checks**: The bot checks the Excel file every 5 minutes to see if seats have become available for the user's preferred course and section.
5. **Notifications**: The bot sends notifications to users based on seat availability.

## User Guide

### Starting the Bot

1. **/start**: This command initializes the bot and welcomes the user.
    ```
    /start
    ```
    **Response**: "Welcome to the NSU Course Notifier Bot! Please use /setpref <course_name> <section> to set your preferred course and section. And then use /check to check the availability."

### Setting Course Preferences

2. **/setpref**: This command allows users to set their preferred course and section.
    ```
    /setpref <course_name> <section>
    ```
    **Example**:
    ```
    /setpref CSE101 1
    ```
    **Response**: "Preference set: CSE101 Section 1"

### Checking Seat Availability

3. **/check**: This command checks the current seat availability for the user's preferred course and section.
    ```
    /check
    ```
    **Response**:
    - If seats are available: "Course: CSE101 Section: 1 Seats Available: X"
    - If no seats are available: "Course: CSE101 Section: 1 Seats Available: 0\nWe will notify you if any seat available within 30 minutes, keep patience."

### Notifications

- **Immediate Notification**: If seats become available within 30 minutes, the bot sends a notification.
    ```
    Seats available for Course: CSE101 Section: 1 - X
    ```
- **No Seat Notification**: If no seats become available within 30 minutes, the bot sends a final notification.
    ```
    No seats became available for Course: CSE101 Section: 1 within 30 minutes. Please try again later.
    ```

## Methodology

### Data Scraping

The bot uses `requests` and `BeautifulSoup` to scrape course data from the NSU website every 10 minutes. The scraped data includes the course name, section, faculty, time, room number, and seat availability.

### Excel File

The scraped data is saved in an `course_data.xlsx` file using `pandas`. This file is updated every 10 minutes to ensure the bot has the latest information.

### Bot Functionality

- **Load Course Data**: The bot loads the course data from the `course_data.xlsx` file.
- **Set Preferences**: Users set their course and section preferences using the `/setpref` command.
- **Check Availability**: The bot checks the seat availability for the user's preferred course and section using the `/check` command.
- **Periodic Checks**: The bot runs periodic checks every 5 minutes to see if seats have become available for the user's preferred course and section.
- **Notifications**: The bot sends notifications to users about seat availability or informs them if no seats are available within 30 minutes.

## Dependencies

- `pandas`
- `requests`
- `BeautifulSoup`
- `telebot`
- `schedule`

## Installation

1. Clone the repository.
    ```bash
    git clone https://github.com/amanullahshah32/Telegram-Bot.git
    cd Telegram-Bot
    ```

2. Install the required packages.
    ```bash
    pip install pandas requests beautifulsoup4 pyTelegramBotAPI schedule
    ```

3. Run the scraping script to initialize the data.
    ```bash
    python scrape.py
    ```

4. Run the bot.
    ```bash
    python bot.py
    ```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License.
