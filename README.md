# Agrofix - Bulk Produce Order Management System

A full-stack web application that facilitates bulk vegetable and fruit orders, built with Next.js, PostgreSQL, and deployed on Vercel.

## Features

- **Product Catalogue**: Browse available vegetables and fruits
- **Order Management**: Place and track bulk orders
- **Admin Dashboard**: Manage inventory and order statuses
- **Responsive Design**: Works on desktop and mobile devices

## Tech Stack

- **Frontend**: Next.js with TypeScript, Tailwind CSS
- **Backend**: Next.js API Routes
- **Database**: PostgreSQL (Neon.tech)
- **Form Handling**: React Hook Form with Zod validation
- **State Management**: React Context API
- **Deployment**: Vercel

## Local Development Setup

### Prerequisites

- Node.js (v16 or later)
- npm or yarn
- PostgreSQL database (local or Neon.tech)

### Installation Steps

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/agrofix.git
   cd agrofix
   ```

2. Install dependencies:
   ```bash
   npm install
   # or
   yarn install
   ```

3. Set up environment variables:
   Create a `.env.local` file in the root directory with the following variables:
   ```
   DATABASE_URL=postgresql://username:password@hostname:port/database
   NEXTAUTH_SECRET=your_random_string_here
   NEXTAUTH_URL=http://localhost:3000
   ```

4. Set up the database:
   ```bash
   npx prisma migrate dev --name init
   ```

5. Start the development server:
   ```bash
   npm run dev
   # or
   yarn dev
   ```

6. Open [http://localhost:3000](http://localhost:3000) in your browser to see the application.

## Database Schema

The application uses the following database schema:

### Products Table
- `id`: UUID (Primary Key)
- `name`: String
- `description`: String
- `price`: Decimal
- `unit`: String (kg, bunch, piece, etc.)
- `inStock`: Boolean
- `imageUrl`: String (optional)
- `createdAt`: DateTime
- `updatedAt`: DateTime

### Orders Table
- `id`: UUID (Primary Key)
- `buyerName`: String
- `buyerContact`: String
- `deliveryAddress`: String
- `items`: JSON (Array of products with quantities)
- `status`: Enum (Pending, In Progress, Delivered)
- `totalAmount`: Decimal
- `createdAt`: DateTime
- `updatedAt`: DateTime

## API Endpoints

### Products
- `GET /api/products` - Get all products
- `POST /api/products` - Add a new product (admin only)
- `PUT /api/products/:id` - Update a product (admin only)
- `DELETE /api/products/:id` - Delete a product (admin only)

### Orders
- `GET /api/orders` - Get all orders (admin only)
- `GET /api/orders/:id` - Get a specific order
- `POST /api/orders` - Create a new order
- `PUT /api/orders/:id` - Update order status (admin only)

## Deployment

The application is deployed on Vercel. To deploy your own instance:

1. Create a Vercel account
2. Connect your GitHub repository
3. Configure environment variables
4. Deploy the application

