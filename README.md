# Company & Event Management System

## 1. Overview
This system is designed to manage companies and their events efficiently. It includes an admin panel for managing companies and an individual company panel for managing events and participants. The system is built using **React.js, Next.js, MongoDB, and Prisma** to ensure scalability, security, and high performance.

---
## 2. Features & Modules

### **Admin Panel**
#### **Authentication**
- Secure login and logout functionality.

#### **Company Management**
- Add new companies with:
  - Company name
  - Username
  - Password (hashed for security)
  - Company logo
  - Initial event details
- View all registered companies.
- Edit company details (name, logo, password).
- Delete companies if needed.

#### **Event Management**
- View all events from all companies.
- View participants of each event.
- Export participant data in **CSV, XLS, PDF** formats.

---
### **Company Panel**
#### **Authentication**
- Company login and logout.

#### **Company Profile Management**
- Update the company logo (Name and Password remain unchanged).

#### **Event Management**
- Create a new event with:
  - Name
  - Description
  - Image
  - Date
- View all company events.
- View participants (without National ID visibility).
- Export event data in **CSV, XLS, PDF** formats.

---
### **Participant Registration Form**
When a company creates an event, a registration form is generated containing:

| Name | National ID / Passport | Mobile Number | Email | University | Faculty | Level | Gender | Age |
|------|-----------------------|---------------|-------|------------|---------|-------|--------|-----|

- Data is saved in the event’s participant list.
- The **admin can view all fields**, while the **company cannot see the National ID**.

---
## 3. Technology Stack

### **Frontend**
- **React.js** → UI components & state management.
- **Next.js** → Server-side rendering & API routes.
- **Tailwind CSS** → Responsive UI.

### **Backend**
- **Next.js API Routes** → Handles authentication & CRUD operations.
- **Prisma ORM** → Manages MongoDB interactions.
- **JWT Authentication** → Secure user sessions.
- **bcrypt.js** → Password hashing.

### **Database (MongoDB)**
#### **Collections & Schema Examples**
##### **Users (Admins & Companies)**
```json
{
  "id": "uuid",
  "name": "Company Name",
  "username": "company_username",
  "password": "hashed_password",
  "logo": "image_url",
  "role": "admin | company"
}
```
##### **Events**
```json
{
  "id": "uuid",
  "companyId": "company_uuid",
  "name": "Event Name",
  "description": "Event details",
  "image": "event_image_url",
  "date": "2025-01-20T12:00:00Z"
}
```
##### **Participants**
```json
{
  "id": "uuid",
  "eventId": "event_uuid",
  "name": "Participant Name",
  "nationalId": "XXXXXX",
  "mobile": "XXXXXXXXXX",
  "email": "example@example.com",
  "university": "University Name",
  "faculty": "Faculty Name",
  "level": "Undergraduate/Postgraduate",
  "gender": "Male/Female",
  "age": "XX"
}
```

### **File Uploads & Data Exporting**
- **Cloudinary** → Stores company logos & event images.
- **xlsx / pdfkit / csv-parser** → Exports participant data.

---
## 4. API Endpoints
### **Authentication**
- `POST /api/auth/login` → Login for admin & companies.
- `POST /api/auth/logout` → Logout session.

### **Admin APIs**
- `GET /api/admin/companies` → List all companies.
- `POST /api/admin/companies` → Create a new company.
- `PATCH /api/admin/companies/:id` → Update company details.
- `DELETE /api/admin/companies/:id` → Delete a company.

### **Company APIs**
- `GET /api/company/events` → List all events for the company.
- `POST /api/company/events` → Create a new event.
- `GET /api/company/events/:id` → View event details.
- `DELETE /api/company/events/:id` → Delete an event.
- `GET /api/company/events/:id/participants` → View participant list.
- `GET /api/company/events/:id/export` → Export participant data.

---
## 5. Project Structure
```
/project-root
│── /src
│   │── /pages
│   │   │── /admin
│   │   │── /company
│   │   │── /events
│   │   │── /api
│   │── /components
│   │── /utils
│── /prisma
│── /public
│── .env
│── package.json
│── next.config.js
```

---
## 6. Deployment
### **Hosting & Services**
- **Vercel** → Deploying Next.js frontend & backend.
- **MongoDB Atlas** → Cloud-based database hosting.
- **AWS S3 / Cloudinary / github** → Secure file storage.



