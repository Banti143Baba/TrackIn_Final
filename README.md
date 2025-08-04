# TrackInTrade 🧠📈

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)

TrackInTrade is a full-featured, AI-driven trading journal designed specifically for retail traders in the Indian stock market. It empowers users to meticulously **record**, **analyze**, and **enhance** their trading performance by providing smart insights based on trade data, emotional patterns, and strategic decisions. Our custom AI/ML pipeline delivers personalized feedback *without* offering any buy/sell recommendations.

---

## ✨ Key Features

* 🔐 **User Authentication**: Secure login and signup system to protect your data.
* ✍️ **Dynamic Journaling**: Easily add, edit, and delete trade entries on the fly.
* 🤖 **AI-Powered Insights**: Receive real-time, intelligent feedback on your trades via the OpenRouter API.
* 📊 **Performance Analytics**: Visualize your performance with a graphical summary, breaking down profitability by instrument, day, and month.
* 📝 **Dedicated Notes**: A separate section for self-reflection, strategy notes, and key learnings.
* 🔒 **Data Isolation**: Each user's data is completely private and accessible only to them.
* ☁️ **Cloud Database**: All data is securely stored on a cloud-hosted PostgreSQL instance from Neon.tech.
* 💾 **Auto-Saving**: Dynamic data updates are handled seamlessly with `PUT` requests, ensuring your entries are always saved.

---

## 🛠️ Tech Stack

* **Frontend**: `HTML`, `CSS`, `JavaScript`
* **Backend**: `NodeJS`, `ExpressJS`
* **Database**: `Neon.tech (PostgreSQL)`
* **AI/ML**: Custom Python pipeline integrated with the **OpenRouter API** for generating insights.
* **Deployment**: Vercel (Frontend) & Render/Other (Backend).

---
---

## 🗃️ Database Schema

The core of our application is the `journal_entries` table, designed to capture every critical aspect of a trade.

| Column                  | Type          | Description                                    |
| ----------------------- | ------------- | ---------------------------------------------- |
| `id`                    | `SERIAL`      | **Primary Key** |
| `user_id`               | `INTEGER`     | Foreign Key (links entry to a specific user)   |
| `trade_date`            | `DATE`        | Date of the trade                              |
| `timeframe`             | `VARCHAR(20)` | e.g., Intraday, Swing                          |
| `stock`                 | `VARCHAR(50)` | Stock name or symbol                           |
| `position_size`         | `NUMERIC`     | Number of shares or lots                       |
| `direction`             | `VARCHAR(10)` | Long / Short                                   |
| `entry_price`           | `NUMERIC`     | Price at entry                                 |
| `entry_time`            | `TIME`        | Time of entry                                  |
| `entry_reason`          | `TEXT`        | Rationale for taking the trade                 |
| `exit_price`            | `NUMERIC`     | Price at exit                                  |
| `exit_time`             | `TIME`        | Time of exit                                   |
| `exit_reason`           | `TEXT`        | Rationale for exiting the trade                |
| `stop_loss_price`       | `NUMERIC`     | Pre-defined stop-loss level                    |
| `target_price`          | `NUMERIC`     | Pre-defined target price                       |
| `risk_reward_ratio`     | `NUMERIC`     | Calculated Risk-to-Reward Ratio (RRR)          |
| `percentage_return`     | `NUMERIC`     | Return in percentage                           |
| `overall_market_trend`  | `VARCHAR(50)` | e.g., Bullish, Bearish, Sideways               |
| `news_impact`           | `TEXT`        | Impact of any related news                     |
| `mistakes`              | `TEXT`        | Any mistakes made during the trade             |
| `what_went_well`        | `TEXT`        | Positive aspects of the trade                  |
| `emotions_during_trade` | `TEXT`        | Self-reflection on emotional state             |
| `improvement_suggestions`| `TEXT`        | Notes on how to improve next time              |
| `created_at`            | `TIMESTAMP`   | Auto-generated timestamp on trade creation     |

---

## 🚀 Getting Started

Follow these instructions to get a local copy up and running.

### Prerequisites

* Python 3.8+
* A [Neon.tech](https://neon.tech/) account for the PostgreSQL database.

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/yourusername/TrackInTrade.git](https://github.com/yourusername/TrackInTrade.git)
    cd TrackInTrade
    ```

2.  **Install the required dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Set up Environment Variables:**
    * Create a new project on [Neon.tech](https://neon.tech/).
    * Find your database credentials (Host, DB Name, User, Password).
    * Create a `.env` file in the root directory and add your credentials.
    
    ```env
    DATABASE_URL="postgresql://user:password@host/dbname"
    OPENROUTER_API_KEY="your_openrouter_api_key"
    FLASK_SECRET_KEY="your_strong_secret_key"
    ```

4.  **Initialize the Database:**
    * You will need to run a script to create the necessary tables based on the schema above. Ensure your `database.py` contains a function to do this.

5.  **Start the Flask Server:**
    ```bash
    python web/app.py
    ```
    The application will be running at `http://127.0.0.1:5000`.

---

## 🛡️ Security

Security is a top priority for TrackInTrade.

* **Authentication**: We use a **session-based login system** to ensure that user sessions are handled securely.
* **Data Isolation**: The backend logic is designed to ensure that a logged-in user can only ever access their own trade entries and notes.
* **No JWT**: For simplicity and robust control, we avoid JWTs. Each browser tab is treated as an individual session entity.

---

## 🚧 Future Improvements

We have an exciting roadmap ahead!

- [ ] **Chart Visualizations**: Integrate Plotly or Chart.js to display trade setups on charts.
- [ ] **Data Export**: Allow users to export their journal data to CSV or PDF formats.
- [ ] **Email Summaries**: Send automated weekly performance summary reports via email.
- [ ] **Automation**: Use Prefect or a cron job for scheduled tasks and data processing.
- [ ] **Mobile Alerts**: Implement real-time mobile notifications for trade events via Twilio.

---

## 📜 License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## 🙋‍♂️ Contact

Developed with 💻 and 📈 by **[AetherStaack]** (AI/ML & Data Logic) and my teammate (Frontend & Backend).
