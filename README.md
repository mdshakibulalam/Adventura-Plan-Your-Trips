# Adventura: Plan Your Trips

**Adventura** is a travel planning website for exploring Bangladesh. Travelers can discover tourist spots, find hotels, build their own trip plans with automatic cost calculation, or book ready-made tour packages. An admin panel manages users, packages and payment approvals.

> Full details are in [`Adventura_Project_Report.pdf`](Adventura_Project_Report.pdf).

## Features

### 👤 User Side

- **Authentication:** Register with name, email, phone number, address and password (with confirmation), then log in securely.
- **Homepage:** Shows rotating reviews of tourist spots for visitors and members.
- **Explore Spots:**
  - Search by spot name or district
  - Pop-up information box with picture, district, available transport and description
  - Comment on spots and view all comments
- **Trip Planning:**
  - Select district, spot and hotel
  - Choose stay dates (the number of nights is counted automatically)
  - Choose your starting location, transport to the destination and return transport
  - Total cost is calculated from hotel cost × nights plus transport and return transport costs
  - View, confirm (pay) or delete your saved plans
- **Hotels:**
  - Search hotels and resorts
  - Comment on hotels
  - View the exact hotel location on an integrated Google Map
- **Packages:**
  - Search ready-made packages by spot
  - Book a package and pay by bKash (phone number and transaction ID)
  - Booking stays in a "waiting for confirmation" state until an admin approves it

### 🛠️ Admin Panel

- Separate admin login
- View all users, update their details (looked up by email) or delete them
- Add and delete tour packages (hotel, spot, transport, days, price)
- Review user package bookings and **approve payments**

## Tech Stack

| Layer      | Technology                                      |
|------------|-------------------------------------------------|
| Backend    | PHP, Laravel (MVC, Eloquent/Query Builder, Artisan) |
| Database   | MySQL (managed with Laravel migrations)         |
| Frontend   | Blade templates, HTML, CSS, JavaScript, jQuery AJAX |
| Maps       | Google Maps embed                               |
| Tools      | Composer, npm, Vite                             |

## Project Structure

```
Adventura-Plan-Your-Trips/
├── app/          # Controllers (Auth, Spots, Hotels, Admin), middleware, models
├── bootstrap/    # Framework bootstrapping
├── config/       # Application configuration
├── database/     # Migrations (spots, districts, hotels, transportations, packages, ...)
├── public/       # Public assets and entry point
├── resources/    # Blade views, CSS, JS
├── routes/       # web.php routes
├── storage/      # Logs, cache, uploads
└── tests/        # Automated tests
```


### Admin Access

The admin logs in from the same login page using a dedicated admin account stored in the `users` table. Create one directly in the database, then log in with that email and password to reach the admin dashboard.

## How It Works

1. A visitor registers or logs in and lands on the dashboard.
2. They explore **Spots** and **Hotels**, leave comments and check hotel locations on the map.
3. In **Trip Plan** they pick a district, spot, hotel, dates and transport, then confirm. The plan appears in their plan list with the total cost, where they can pay or delete it.
4. In **Package** they search for a spot, book a ready-made package and submit their bKash payment details.
5. The admin reviews the payment and approves the booking.
