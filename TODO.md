# Forgot Password with OTP Implementation

## Backend Tasks
- [x] Install nodemailer dependency
- [x] Add OTP fields to User model (otp, otpExpires)
- [x] Implement forgotPassword function in authController
- [x] Implement verifyOTP function in authController
- [x] Implement resetPassword function in authController
- [x] Add forgot password routes to authRoutes.js

## Frontend Tasks
- [x] Create ForgotPassword.jsx component
- [x] Add forgot password link to Login.jsx
- [x] Add forgot password methods to AuthContext.jsx
- [x] Add forgot password routes to App.jsx

## Testing & Validation
- [ ] Set up email environment variables (EMAIL_USER, EMAIL_PASS)
- [ ] Test OTP email sending
- [ ] Test complete forgot password flow
- [ ] Handle edge cases (expired OTP, invalid email, etc.)
