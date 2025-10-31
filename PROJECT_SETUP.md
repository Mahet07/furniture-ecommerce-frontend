# FurniHub - E-commerce Furniture Platform

A modern, full-stack e-commerce application for selling furniture, built with React, TypeScript, and Spring Boot backend.

## 🚀 Features

### Customer Features
- **Browse Products**: Explore a wide range of furniture with filtering and search capabilities
- **Product Details**: View detailed information, images, and specifications
- **Shopping Cart**: Add items, manage quantities, and view cart summary
- **Secure Checkout**: Razorpay payment integration for safe transactions
- **User Dashboard**: Track orders and view order history
- **Authentication**: JWT-based secure login and registration

### Admin Features
- **Product Management**: Add, edit, and delete products
- **Order Management**: View and update order statuses
- **Inventory Control**: Track stock levels
- **Dashboard Analytics**: Overview of sales and orders

### UI/UX Features
- **Responsive Design**: Fully mobile-friendly interface
- **Dark/Light Mode**: Toggle between themes
- **Smooth Animations**: Framer Motion powered transitions
- **Beautiful Design**: Premium furniture store aesthetic with Tailwind CSS

## 📦 Tech Stack

### Frontend
- **React 18** with TypeScript
- **Vite** for blazing fast builds
- **Tailwind CSS** for styling
- **shadcn/ui** for UI components
- **Framer Motion** for animations
- **React Router v6** for navigation
- **Axios** for API calls
- **React Context API** for state management

### Backend Integration
- **Spring Boot** REST APIs
- **JWT Authentication**
- **Razorpay** payment gateway

## 🛠️ Installation & Setup

### Prerequisites
- Node.js 18+ and npm
- Spring Boot backend running (separate repository)
- Razorpay account for payments

### Frontend Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd furnihub-frontend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   
   Create a `.env` file in the root directory:
   ```env
   VITE_API_BASE_URL=https://furniture-ecommerce-backend-production-bac7.up.railway.app/api
   VITE_RAZORPAY_KEY_ID=your_razorpay_key_id
   ```

4. **Start development server**
   ```bash
   npm run dev
   ```
   
   The app will be available at `https://furniture-ecommerce-backend-production-bac7.up.railway.app`

5. **Build for production**
   ```bash
   npm run build
   ```

## 📁 Project Structure

```
src/
├── components/          # Reusable UI components
│   ├── ui/             # shadcn/ui components
│   ├── Navbar.tsx      # Navigation bar
│   ├── Footer.tsx      # Footer component
│   ├── ProductCard.tsx # Product card component
│   └── ProtectedRoute.tsx # Route protection
├── pages/              # Page components
│   ├── Home.tsx        # Landing page
│   ├── Products.tsx    # Product catalog
│   ├── ProductDetail.tsx # Product details
│   ├── Cart.tsx        # Shopping cart
│   ├── Checkout.tsx    # Checkout page
│   ├── Login.tsx       # Auth page
│   ├── Dashboard.tsx   # User dashboard
│   └── AdminDashboard.tsx # Admin panel
├── context/            # React Context providers
│   ├── AuthContext.tsx # Authentication state
│   ├── CartContext.tsx # Shopping cart state
│   └── ThemeContext.tsx # Theme management
├── lib/                # Utility functions
│   ├── api.ts          # Axios instance
│   └── utils.ts        # Helper functions
├── hooks/              # Custom React hooks
└── index.css           # Global styles & design system
```

## 🎨 Design System

The project uses a custom design system with:
- **Warm earth tones** for furniture aesthetic
- **Semantic color tokens** defined in `index.css`
- **Consistent spacing** and typography
- **Custom animations** for smooth UX
- **Responsive breakpoints** for all devices

### Color Palette
- Primary: Warm wood brown (#B8865F)
- Secondary: Sage green
- Accent: Forest green
- Background: Warm beige

## 🔌 Backend API Integration

### Required Endpoints

#### Authentication
- `POST /api/auth/signup` - User registration
- `POST /api/auth/signin` - User login

#### Products
- `GET /api/products` - Get all products
- `GET /api/products/:id` - Get product details
- `POST /api/admin/products` - Add product (Admin)
- `PUT /api/admin/products/:id` - Update product (Admin)
- `DELETE /api/admin/products/:id` - Delete product (Admin)

#### Orders
- `POST /api/orders/create` - Create order
- `POST /api/orders/verify` - Verify payment
- `GET /api/orders/user` - Get user orders
- `GET /api/admin/orders` - Get all orders (Admin)
- `PUT /api/admin/orders/:id` - Update order status (Admin)

### API Response Format

**Login Response:**
```json
{
  "token": "jwt_token_here",
  "user": {
    "id": "user_id",
    "name": "User Name",
    "email": "user@email.com",
    "role": "CUSTOMER" | "ADMIN"
  }
}
```

**Product Response:**
```json
{
  "id": "product_id",
  "name": "Product Name",
  "price": 45999,
  "category": "Dining",
  "stock": 10,
  "description": "Product description",
  "imageUrl": "image_url"
}
```

## 💳 Razorpay Integration

1. **Create Razorpay account** at https://razorpay.com
2. **Get API keys** from dashboard
3. **Add key to environment variables**
4. **Backend must generate order** and return `razorpayOrderId`
5. **Frontend handles payment** and sends verification to backend

### Payment Flow
1. User fills shipping info and clicks "Pay"
2. Frontend creates order on backend
3. Razorpay checkout modal opens
4. User completes payment
5. Backend verifies payment signature
6. Order is confirmed

## 🔒 Authentication

- JWT tokens stored in localStorage
- Automatic token injection in API requests
- Protected routes for authenticated users
- Role-based access control (Admin/Customer)
- Auto-redirect on token expiration

## 📱 Responsive Design

- Mobile-first approach
- Breakpoints: sm (640px), md (768px), lg (1024px), xl (1280px)
- Touch-friendly UI elements
- Optimized images and lazy loading

## 🚀 Deployment

### Frontend Deployment (Netlify/Vercel)

1. **Build the project**
   ```bash
   npm run build
   ```

2. **Deploy to Netlify**
   - Connect your GitHub repository
   - Set build command: `npm run build`
   - Set publish directory: `dist`
   - Add environment variables in Netlify dashboard

3. **Deploy to Vercel**
   ```bash
   npm install -g vercel
   vercel
   ```

### Environment Variables for Production
```env
VITE_API_BASE_URL=https://your-backend-api.com/api
VITE_RAZORPAY_KEY_ID=your_production_razorpay_key
```

## 🧪 Testing

**Test User Credentials:**
- Email: test@example.com
- Password: password123

**Test Admin Credentials:**
- Email: admin@furnihub.com
- Password: admin123

## 📝 Development Guidelines

1. **Code Style**: Use TypeScript strict mode
2. **Components**: Keep components small and focused
3. **State Management**: Use Context API for global state
4. **Styling**: Use Tailwind CSS utility classes
5. **Design System**: Always use semantic tokens from index.css
6. **API Calls**: Use the configured axios instance from `lib/api.ts`
7. **Error Handling**: Show user-friendly error messages with toast notifications

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License.

## 📞 Support

For support, email support@furnihub.com or open an issue in the repository.

## 🎯 Future Enhancements

- [ ] Product reviews and ratings
- [ ] Wishlist functionality
- [ ] Advanced filtering (price range, color, material)
- [ ] Product recommendations
- [ ] Email notifications
- [ ] Social media sharing
- [ ] Multi-currency support
- [ ] AR furniture preview
- [ ] Chat support integration

---

Built with ❤️ using React, TypeScript, and Tailwind CSS
