# 🏟️ Sports Hall Booking System – ServiceNow Widget

> A complete sports venue booking widget for ServiceNow Service Portal with interactive UI, booking flow, and local storage persistence.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Flow Diagram](#flow-diagram)
- [Installation](#installation)
- [Widget Structure](#widget-structure)
- [Customization](#customization)
- [Demo](#demo)
- [License](#license)

---

## 🎯 Overview

The **Sports Hall Booking System** is a fully functional ServiceNow Service Portal widget that allows users to browse, select, and book sports venues in real-time. It provides an intuitive booking flow with instant confirmation, payment simulation, and booking management capabilities.

### Built For:
- 🏢 ServiceNow Service Portal
- 🎯 Sports Hall Management
- 📅 Venue Booking Systems
- 🏆 Community Sports Centers

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🎯 **Sport Selection** | Choose from multiple sports (Badminton, Tennis, Cricket, Football, Basketball, Swimming) |
| 💳 **Payment Simulation** | Complete booking flow with payment processing simulation |
| 📋 **Booking Management** | View all your bookings with status and details |
| 🗺️ **Explore Venues** | Browse all available venues with prices and book directly |
| 📱 **Responsive Design** | Works on all screen sizes (desktop, tablet, mobile) |
| 💾 **Local Storage** | Bookings persist across sessions using browser localStorage |
| ⚡ **Visual Flow** | Step-by-step booking progress indicator |
| 🔔 **Email Simulation** | Confirmation email notification with venue details |
| 🎨 **Modern UI** | Clean, professional design with animations |

---

## 🔄 Flow Diagram

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         SPORTS HALL BOOKING SYSTEM                         │
│                                   FLOW DIAGRAM                              │
└─────────────────────────────────────────────────────────────────────────────┘

                                    ┌──────────────────┐
                                    │    USER PORTAL    │
                                    │   (ServiceNow)    │
                                    └────────┬─────────┘
                                             │
                                    ┌────────▼─────────┐
                                    │  User Opens       │
                                    │  Service Portal   │
                                    └────────┬─────────┘
                                             │
                                    ┌────────▼─────────┐
                                    │  Login /          │
                                    │  Authentication   │
                                    └────────┬─────────┘
                                             │
                                    ┌────────▼─────────┐
                                    │  Browse Available │
                                    │  Sports Halls &   │
                                    │  Time Slots       │
                                    └────────┬─────────┘
                                             │
                                    ┌────────▼─────────┐
                                    │  Select Hall,     │
                                    │  Date & Time Slot │
                                    └────────┬─────────┘
                                             │
                                    ┌────────▼─────────┐
                                    │  Fill Booking     │
                                    │  Details          │
                                    └────────┬─────────┘
                                             │
                                    ┌────────▼─────────┐
                                    │  Submit Booking   │
                                    │  Request          │
                                    └────────┬─────────┘
                                             │
                            ┌────────────────▼────────────────┐
                            │          SYSTEM                 │
                            │    AVAILABILITY CHECK           │
                            └────────────────┬────────────────┘
                                             │
                                    ┌────────▼─────────┐
                                    │  System Checks    │
                                    │  Availability in  │
                                    │  Real Time        │
                                    └────────┬─────────┘
                                             │
                              ┌──────────────▼──────────────┐
                              │      BOOKING & WORKFLOW      │
                              │        (ServiceNow)          │
                              └──────────────┬──────────────┘
                                             │
                                    ┌────────▼─────────┐
                                    │  Slot Available? │
                                    └────────┬─────────┘
                                             │
                      ┌──────────────────────┼──────────────────────┐
                      │ YES                  │ NO                   │
                      ▼                      ▼                      ▼
              ┌───────────────┐    ┌─────────────────┐    ┌─────────────┐
              │ Create        │    │ Notify User –   │    │    END      │
              │ Booking       │    │ Booking Rejected│    │             │
              │ Record        │    └─────────────────┘    └─────────────┘
              └───────┬───────┘
                      │
              ┌───────▼───────┐
              │ ServiceNow    │
              │ Workflow      │
              │ Triggered     │
              └───────┬───────┘
                      │
              ┌───────▼───────┐
              │ Approval      │
              │ Required?     │
              └───────┬───────┘
                      │
       ┌──────────────┼──────────────┐
       │ YES          │ NO           │
       ▼              ▼              ▼
┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│ Approval    │ │ Send Email  │ │ Send Email  │
│ Process     │ │ Confirmation│ │ Confirmation│
└──────┬──────┘ │ Notification│ │ Notification│
       │        └──────┬──────┘ └──────┬──────┘
       ▼               │               │
┌─────────────┐        │               │
│ Approved?   │        │               │
└──────┬──────┘        │               │
       │               │               │
  ┌────┼────┐          │               │
  │ YES│ NO │          │               │
  ▼    ▼    ▼          ▼               ▼
┌───┐ ┌───┐ ┌─────────────────────────────────┐
│   │ │   │ │           PAYMENT               │
│   │ │   │ │         (Optional)              │
└───┘ └───┘ └───────────────┬─────────────────┘
  │     │                   │
  ▼     ▼                   ▼
┌─────────────┐ ┌─────────────────────────────────┐
│ Notify User │ │    Online Payment Processing    │
│ – Booking   │ │      (If Applicable)            │
│ Rejected    │ └───────────────┬─────────────────┘
└─────────────┘                 │
                                ▼
                      ┌─────────────────────┐
                      │ Update Booking      │
                      │ Status & Calendar   │
                      └──────────┬──────────┘
                                 │
                      ┌──────────▼──────────┐
                      │ Store Booking Data  │
                      │ for Reports &       │
                      │ Analytics           │
                      └──────────┬──────────┘
                                 │
                      ┌──────────▼──────────┐
                      │     COMPLETE         │
                      └─────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│                              LEGEND                                         │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐            │
│  │ 🟦 User Actions  │  │ 🟩 System        │  │ 🟨 Workflow /   │            │
│  │                  │  │   Actions        │  │   Approval      │            │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘            │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐            │
│  │ 🟪 Notifications │  │ 🟧 Payment       │  │ 🟥 Exception /  │            │
│  │                  │  │   (Optional)     │  │   Alternate     │            │
│  └─────────────────┘  └─────────────────┘  │   Flow          │            │
│                                             └─────────────────┘            │
│  ┌─────────────────┐  ┌─────────────────┐                                 │
│  │ 📊 Data /        │  │ 🔶 Decision      │                                 │
│  │   Records        │  │   Point          │                                 │
│  └─────────────────┘  └─────────────────┘                                 │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 📁 Widget Structure

```
sports-zone-widget/
├── README.md                 # This file
├── html-template.html        # HTML structure
├── css-scss.scss            # All styles (SCSS)
├── client-script.js         # JavaScript logic
├── server-script.js         # Server-side data
├── link-function.js         # AngularJS link function
├── widget-config.json       # Widget configuration
└── preview/
    └── screenshot.png       # Widget preview image
```

---

## 🚀 Installation

### ServiceNow Service Portal

1. Navigate to **Service Portal > Widgets**
2. Click **New**
3. Enter the following details:
   - **Name**: `Sports Zone Booking`
   - **ID**: `sports-zone-booking`
   - **Description**: `Complete sports venue booking widget`

4. Copy the code from each file into the corresponding section:

| File | Section in Widget Editor |
|------|--------------------------|
| `html-template.html` | HTML Template |
| `css-scss.scss` | CSS - SCSS |
| `client-script.js` | Client Script |
| `server-script.js` | Server Script |
| `link-function.js` | Link Function |

5. Click **Save**

### Add to Portal Page

1. Open your Service Portal page in **Page Designer**
2. Click **Add Widget**
3. Search for `Sports Zone Booking`
4. Drag and drop the widget to your page
5. Click **Save** and **Publish**

---

## 🎨 Customization

### Add a New Sport

**1. Update HTML Template:**
```html
<div class="sport-item" data-sport="YourSport">
    <input type="radio" name="sport" id="sportYourSport" value="YourSport" />
    <span class="sport-icon">🏐</span>
    <label for="sportYourSport">Your Sport</label>
    <span class="sport-badge">$XX</span>
</div>
```

**2. Update Client Script:**
```javascript
// Add to prices object
var prices = {
    // ... existing sports
    YourSport: 25.00
};

// Add to venues object
var venues = {
    // ... existing venues
    YourSport: 'Your Sport Venue 🏐'
};

// Add to emojis object
var emojis = {
    // ... existing emojis
    YourSport: '🏐'
};

// Add to allVenues array
var allVenues = [
    // ... existing venues
    { name: 'Your Sport Venue', icon: '🏐', price: '$25/hr' }
];
```

### Change Colors

Update the SCSS variables at the top of the `css-scss.scss` file:
```scss
$primary: #1a7ae4;      // Main blue color
$secondary: #0a2540;    // Dark blue/navy
$accent: #ffd700;       // Gold accent
$success: #0f973d;      // Green for success
$warning: #f5a623;      // Orange for warnings
```

### Change Currency Symbol

Update in `client-script.js`:
```javascript
// Find and replace '$' with your currency
// Example: '€' for Euro
displayAmount.textContent = '€' + price.toFixed(2);
```

---

## 🔧 Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| `show_help` | Show help section | `true` |
| `enable_bookings` | Enable booking functionality | `true` |
| `currency` | Currency symbol | `$` |
| `payment_timeout` | Payment processing delay (ms) | `1800` |
| `max_bookings` | Maximum bookings per user | `Unlimited` |

---

## 📱 Responsive Design

| Breakpoint | Layout |
|------------|--------|
| > 850px | Two-column layout (Sport Selection + Payment) |
| 481px - 850px | Single column, adjusted spacing |
| < 480px | Stacked layout, smaller cards |

---

## 🛠️ Technologies Used

- **Frontend**: HTML5, CSS3, SCSS
- **JavaScript**: Vanilla JS (ES6)
- **Framework**: ServiceNow Service Portal (AngularJS)
- **Icons**: Font Awesome 6
- **Storage**: LocalStorage API
- **Animations**: CSS Animations

---

## 📝 Flow Steps Explained

### 1. User Actions (Portal)
- User opens Service Portal
- Login/Authentication
- Browse available sports halls
- Select hall, date & time
- Fill booking details
- Submit booking request

### 2. System Actions
- System checks availability in real-time
- Validates selected slot

### 3. Booking & Workflow
- Creates booking record
- Triggers ServiceNow workflow
- Approval process (if required)
- Sends confirmation email
- Processes payment (optional)

### 4. Notifications
- User notified on approval
- User notified on rejection
- Confirmation email sent

### 5. Data Management
- Booking data stored
- Analytics and reporting
- Calendar updated

---

## 🌐 Demo

### Live Demo
🔗 **[View Demo](https://your-demo-link.com)** *


### Demo Features
- ✅ Interactive sport selection
- ✅ Real-time booking simulation
- ✅ Payment processing simulation
- ✅ Booking history view
- ✅ Responsive design demonstration

---


## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push: `git push origin feature/amazing-feature`
5. Open a Pull Request

---

## 📄 License

MIT License - Feel free to use and modify for your projects.

---

## 🙏 Acknowledgments

- ServiceNow Service Portal Team
- Font Awesome for icons
- All contributors and testers

---

## 📈 Roadmap

- [ ] Integration with ServiceNow Calendar
- [ ] Email notifications via ServiceNow
- [ ] Admin dashboard for venue management
- [ ] Multi-language support
- [ ] Payment gateway integration
- [ ] QR code booking confirmation

---

**Built with ❤️ for ServiceNow Service Portal**

---

*Last Updated: 2026*