# AirBnb Clone Project

A robust backend system for a property rental marketplace platform, similar to Airbnb.

## Table of Contents

- [Overview](#overview)
- [Core Features](#core-features)
- [Technical Architecture](#technical-architecture)
- [API Documentation](#api-documentation)

## Overview

This backend system powers a property rental marketplace where users can list, search, and book properties. The system supports multiple user roles (guests, hosts, admins) and provides comprehensive property management, booking, and payment features.

## Core Features

### User Management

- **Authentication**
  - Email/password registration and login
  - OAuth2.0 social login (Google, Facebook)
  - JWT-based session management
  - Role-based access control (Guest, Host, Admin)

- **Profile Management**
  - Profile information updates
  - Profile photo management
  - Preference settings
  - Activity history

### Property Management

- **Listing Features**
  - Property creation and management
  - Multi-image upload
  - Availability calendar
  - Pricing management
  - Amenity selection

- **Search Capabilities**
  - Location-based search
  - Advanced filtering (price, guests, amenities)
  - Real-time availability checking
  - Pagination support

### Booking System

- **Booking Management**
  - Real-time availability verification
  - Double-booking prevention
  - Booking modification/cancellation
  - Status tracking (pending, confirmed, completed, cancelled)
  - Calendar synchronization

### Payment Integration

- **Payment Processing**
  - Secure payment gateway integration (Stripe/PayPal)
  - Multi-currency support
  - Automated host payouts
  - Refund processing
  - Security deposit handling

### Reviews & Ratings

- Review submission with photos
- Rating system (1-5 stars)
- Host responses
- Moderation system
- Analytics and reporting

### Notifications

- **Multi-channel Notifications**
  - Email notifications
  - In-app notifications
  - SMS alerts (optional)
  - Push notifications
  - Custom notification preferences

### Admin Dashboard

- User management
- Property moderation
- Booking oversight
- Payment monitoring
- Analytics and reporting
- System configuration

## Technical Architecture

### Database Schema

```sql
-- Core tables (simplified schema)
Users (
    id, email, password_hash, role, profile_data, created_at, updated_at
)

Properties (
    id, host_id, title, description, location, price, amenities, created_at, updated_at
)

Bookings (
    id, property_id, guest_id, check_in, check_out, status, created_at, updated_at
)

Reviews (
    id, booking_id, rating, comment, photos, created_at, updated_at
)

Payments (
    id, booking_id, amount, currency, status, created_at, updated_at
)
```

### Technology Stack

- **Backend Framework**: Python/FastAPI
- **Database**: PostgreSQL
- **Caching**: Redis
- **Search**: Elasticsearch
- **File Storage**: AWS S3/Cloudinary
- **Authentication**: JWT, OAuth2.0

### Security Measures

- HTTPS/TLS encryption
- Password hashing (bcrypt)
- JWT token management
- Rate limiting
- SQL injection prevention
- XSS protection
- CSRF tokens

## API Documentation

### Authentication Endpoints
```yaml
POST /api/v1/auth/register
POST /api/v1/auth/login
POST /api/v1/auth/refresh-token
POST /api/v1/auth/forgot-password
```

### Property Endpoints
```yaml
GET    /api/v1/properties
POST   /api/v1/properties
GET    /api/v1/properties/:id
PUT    /api/v1/properties/:id
DELETE /api/v1/properties/:id
```

### Booking Endpoints
```yaml
POST   /api/v1/bookings
GET    /api/v1/bookings/:id
PUT    /api/v1/bookings/:id
DELETE /api/v1/bookings/:id
```
