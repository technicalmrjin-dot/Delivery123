# QuickDeliver - Food & Delivery Platform

## Overview

QuickDeliver is a comprehensive delivery platform that enables users to order from restaurants, grocery stores, pharmacies, and electronics vendors. The system supports multiple user roles (customers, riders, and admins) with role-based interfaces and functionalities. The platform features real-time order tracking, vendor management, and a rider dispatch system with cash-on-delivery payment processing.

**Current Status (August 2025):** Fully functional delivery platform with working authentication, admin dashboard with order statistics, rider interface with order management, and customer interface with vendor browsing. All three user roles are implemented and functional with sample data for testing.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
The application uses a React-based single-page application built with TypeScript and Vite for development. The frontend implements a role-based routing system that renders different layouts and pages based on user authentication and role:

- **Customer Interface**: Responsive web app with vendor browsing, cart management, and order tracking
- **Rider Interface**: Dashboard for managing delivery assignments and status updates
- **Admin Interface**: Management panel for overseeing orders, vendors, riders, and platform analytics

The UI is built using shadcn/ui components with Radix UI primitives and styled with Tailwind CSS. State management is handled through React Query for server state and React Context for authentication state.

### Backend Architecture
The backend follows a RESTful API design using Express.js with TypeScript. Key architectural decisions include:

- **Monolithic Structure**: Single Express server handling all API endpoints for simplicity
- **In-Memory Storage**: Currently uses a mock storage interface that can be easily replaced with database integration
- **JWT Authentication**: Token-based authentication with role-based access control
- **Middleware Pipeline**: Request logging, error handling, and authentication middleware

The server structure separates concerns with dedicated modules for routing, storage abstraction, and development tooling.

### Data Storage Solutions
The application currently uses in-memory storage with a mock storage interface that can be easily replaced with database integration. The storage system supports:

- **User Management**: Multi-role user system (customers, riders, admins) with JWT authentication
- **Vendor System**: Restaurant and store management with menu items and categories
- **Order Processing**: Complete order lifecycle from creation to delivery with status tracking
- **Location Tracking**: Address and location data for delivery routing
- **Sample Data**: Pre-seeded demo users, vendors, orders, and rider statistics for testing

The storage interface is designed to handle complex relationships between users, vendors, orders, and delivery assignments while maintaining data integrity. Demo credentials: admin@quickdeliver.com/admin123, rider@quickdeliver.com/rider123, customer@quickdeliver.com/customer123.

### Authentication and Authorization
Authentication is implemented using JWT tokens with the following approach:

- **Role-Based Access**: Three distinct user roles with different permissions
- **Token Storage**: JWT tokens stored in localStorage with automatic refresh handling
- **Protected Routes**: Frontend route protection based on authentication state and user role
- **API Security**: Backend endpoints protected with authentication middleware

The system validates user roles on both frontend and backend to ensure proper access control.

## External Dependencies

### UI and Styling
- **Radix UI**: Provides accessible, unstyled component primitives for complex UI patterns
- **Tailwind CSS**: Utility-first CSS framework for rapid styling and responsive design
- **shadcn/ui**: Pre-built component library combining Radix UI with Tailwind CSS
- **Lucide React**: Icon library for consistent iconography throughout the application

### State Management and Data Fetching
- **TanStack React Query**: Server state management with caching, synchronization, and background updates
- **React Hook Form**: Form state management with validation
- **Zod**: Schema validation for form inputs and API responses

### Database and ORM
- **Drizzle ORM**: Type-safe SQL ORM for database operations with PostgreSQL
- **Neon Database**: Serverless PostgreSQL hosting (configured via DATABASE_URL)

### Authentication and Security
- **bcryptjs**: Password hashing for secure user credential storage
- **jsonwebtoken**: JWT token generation and verification for stateless authentication

### Development and Build Tools
- **Vite**: Fast development server and build tool with hot module replacement
- **TypeScript**: Type safety and enhanced developer experience
- **ESBuild**: Fast JavaScript bundler for production builds

### Routing and Navigation
- **Wouter**: Lightweight routing library for single-page application navigation

The application is configured to run in development mode with hot reloading and can be built for production deployment with optimized assets.