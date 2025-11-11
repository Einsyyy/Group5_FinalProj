# Group5_FinalProj

**UE - CALOOCAN: Engineering Borrowing System**
- The purpose of this proposal is to provide a system for borrowing materials from different departments in a more organized and efficient way. It allows the process of borrowing materials faster and easier to manage for both the students and administrators.

---

## 📋Project Proposal Link
[View project proposal](https://docs.google.com/document/d/1C1Fj5pqExZpKPn4mpm2bcv4sN5IOBOHy_f1UPy8jEzI/edit?usp=sharing)

## Figma Prototype Link
[View Figma Prototype](https://www.figma.com/design/n0EnTU04S89XkaVkO9EXfT/Untitled?node-id=2-55&t=KCDde4V3du0Zy3dX-1)

---
# Engineering Borrowing System

A Blazor Server application for managing laboratory tool borrowing across engineering departments at the University of the East - Caloocan. Features role-based access control, inventory management, and a complete borrowing workflow from request to return.

---

## 🏗️ Project Structure

### System Architecture

```
Group5/
├── Components/
│   ├── Pages/
│   │   ├── Auth/
│   │   │   ├── Home.razor              # Login Page (/)
│   │   │   ├── Signup.razor            # Registration Page (/signup)
│   │   │   ├── VerifyEmail.razor       # Email Verification (/verify-email)
│   │   │   ├── ForgotPassword.razor    # Password Reset Request (/forgot-password)
│   │   │   ├── VerifyResetCode.razor   # Reset Code Verification (/verify-reset-code)
│   │   │   └── ResetPassword.razor     # Password Reset (/reset-password)
│   │   ├── Students/
│   │   │   ├── StudentDashboard.razor  # Student Dashboard (/studentdashboard)
│   │   │   ├── StudentBorrow.razor      # Browse Departments (/studentborrow)
│   │   │   ├── Cart.razor              # Shopping Cart (/cart)
│   │   │   ├── StudentHistory.razor    # Borrowing History (/studenthistory)
│   │   │   ├── ECE.razor               # Electronics Toolroom (/electronics)
│   │   │   ├── EE.razor                # Electrical Toolroom (/electrical)
│   │   │   ├── CHEM.razor              # Chemistry Lab (/chemistry)
│   │   │   ├── CE.razor                # Civil Engineering (/civil)
│   │   │   └── P6.razor                # Physics Lab (/physics)
│   │   ├── Professor/
│   │   │   ├── ProfessorDashboard.razor # Professor Dashboard (/professordashboard)
│   │   │   └── ProfessorForms.razor     # Pending Forms (/professorforms)
│   │   ├── Admin/
│   │   │   ├── AdminDashboard.razor    # Admin Dashboard (/admindashboard)
│   │   │   ├── AdminForms.razor         # Approve Forms (/adminforms)
│   │   │   ├── AdminHistory.razor       # Borrowing History (/adminhistory)
│   │   │   ├── AdminStock.razor         # Inventory Management (/adminstock)
│   │   │   ├── AdminIssue.razor         # Issue Items (/adminissue)
│   │   │   ├── AdminReturns.razor       # Process Returns (/adminreturns)
│   │   │   ├── VerifyBorrowList.razor   # Verify Request (/verifyborrowlist)
│   │   │   ├── OfficialBorrowList.razor # Official Records (/officialborrowlist)
│   │   │   ├── ViewDatabase.razor       # Database View (/viewdatabase)
│   │   │   └── AdminItems.razor         # Item Management (/adminitems)
│   │   ├── Base/
│   │   │   ├── BasePage.cs             # Base class for all pages
│   │   │   ├── BaseToolroomPage.cs     # Base for toolroom pages
│   │   │   └── BaseAdminPage.cs        # Base for admin pages
│   │   └── Shared/
│   │       ├── Aboutus.razor            # About Page (/about-us)
│   │       ├── Help.razor               # Help Page (/help)
│   │       └── Error.razor              # Error Handling (/Error)
│   ├── Layout/
│   │   └── MainLayout.razor             # Main Application Layout
│   ├── Routes.razor                     # Routing Configuration
│   ├── App.razor                        # Root Application Component
│   └── _Imports.razor                   # Global Using Statements
├── Models/
│   ├── User.cs                          # User Account Model
│   ├── InventoryItem.cs                 # Tool/Item Model
│   ├── BorrowForm.cs                    # Borrow Request Model
│   ├── BorrowFormItem.cs                # Items in Borrow Form
│   ├── CartItem.cs                      # Shopping Cart Item
│   ├── BorrowedItem.cs                  # Issued Item Record
│   ├── OfficialBorrowListRecord.cs      # Official Borrow Record
│   ├── TempSignup.cs                    # Temporary Signup Data
│   └── VerificationCode.cs              # Email Verification Codes
├── Data/
│   ├── AppDbContext.cs                  # Entity Framework Context
│   └── Repositories/
│       ├── IRepository.cs               # Generic Repository Interface
│       ├── Repository.cs                 # Generic Repository Implementation
│       ├── IInventoryRepository.cs      # Inventory Repository Interface
│       └── InventoryRepository.cs       # Inventory Repository Implementation
├── Services/
│   ├── Interfaces/
│   │   ├── IEmailService.cs             # Email Service Interface
│   │   └── IInventoryService.cs         # Inventory Service Interface
│   ├── EmailService.cs                   # SMTP Email Service
│   ├── InventoryService.cs               # Inventory Management Service
│   ├── Business/
│   │   ├── CartManager.cs               # Shopping Cart Logic
│   │   └── BorrowManager.cs             # Borrow Request Logic
│   └── Helpers/
│       └── SecurityHelper.cs             # Password Hashing & Validation
├── Shared/
│   ├── UserSession.cs                    # Session Management
│   └── UserDatabase.cs                  # Shared Static Data
├── wwwroot/
│   ├── images/
│   │   └── Apparatus/                   # Tool Images by Department
│   ├── css/
│   │   ├── admin-modern.css             # Admin Page Styles
│   │   └── shared-auth.css              # Auth Page Styles
│   └── app.css                          # Application Styles
├── Program.cs                            # Application Configuration & Startup
└── README.md                             # This File
```

---

## 🔄 Routing System

### Page Route Configuration

| Page | Route | Component | Purpose |
|------|-------|-----------|---------|
| **Authentication** |
| Login | `/` | Home.razor | Primary authentication entry point |
| Signup | `/signup` | Signup.razor | User registration form |
| Verify Email | `/verify-email` | VerifyEmail.razor | Email verification |
| Forgot Password | `/forgot-password` | ForgotPassword.razor | Password reset request |
| Verify Reset Code | `/verify-reset-code` | VerifyResetCode.razor | Reset code verification |
| Reset Password | `/reset-password` | ResetPassword.razor | New password entry |
| **Student Pages** |
| Dashboard | `/studentdashboard` | StudentDashboard.razor | Student home page |
| Browse | `/studentborrow` | StudentBorrow.razor | Department selection |
| Cart | `/cart` | Cart.razor | Shopping cart review |
| History | `/studenthistory` | StudentHistory.razor | Borrowing history |
| Electronics | `/electronics` | ECE.razor | Electronics toolroom |
| Electrical | `/electrical` | EE.razor | Electrical toolroom |
| Chemistry | `/chemistry` | CHEM.razor | Chemistry laboratory |
| Civil | `/civil` | CE.razor | Civil engineering toolroom |
| Physics | `/physics` | P6.razor | Physics laboratory |
| **Professor Pages** |
| Dashboard | `/professordashboard` | ProfessorDashboard.razor | Professor home page |
| Forms | `/professorforms` | ProfessorForms.razor | Review pending requests |
| **Admin Pages** |
| Dashboard | `/admindashboard` | AdminDashboard.razor | Admin home page |
| Forms | `/adminforms` | AdminForms.razor | Approve/issue items |
| History | `/adminhistory` | AdminHistory.razor | Complete history |
| Stock | `/adminstock` | AdminStock.razor | Inventory management |
| Issue | `/adminissue` | AdminIssue.razor | Issue items to students |
| Returns | `/adminreturns` | AdminReturns.razor | Process item returns |
| Verify | `/verifyborrowlist` | VerifyBorrowList.razor | Verify borrow request |
| Official List | `/officialborrowlist` | OfficialBorrowList.razor | Official records |
| Database | `/viewdatabase` | ViewDatabase.razor | Database viewer |
| Items | `/adminitems` | AdminItems.razor | Item management |
| **Shared Pages** |
| About | `/about-us` | Aboutus.razor | System information |
| Help | `/help` | Help.razor | User guide |
| Error | `/Error` | Error.razor | Error handling |

### Routing Implementation

**Routes.razor - Central Routing Configuration**

```razor
<Router AppAssembly="typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="routeData" DefaultLayout="typeof(Layout.MainLayout)" />
        <FocusOnNavigate RouteData="routeData" Selector="h1" />
    </Found>
    <NotFound>
        <LayoutView Layout="typeof(Layout.MainLayout)">
            <p role="alert">Sorry, there's nothing at this address.</p>
        </LayoutView>
    </NotFound>
</Router>
```

**Key Features:**
- ✅ **Assembly Scanning**: Automatically discovers all `@page` directives
- ✅ **Layout Application**: Applies MainLayout to all pages
- ✅ **Focus Management**: Sets focus to `<h1>` elements for accessibility
- ✅ **404 Handling**: Graceful handling of invalid routes
- ✅ **Role-Based Access**: Pages check user roles before rendering

**Navigation Service - Programmatic Routing**

```csharp
@inject NavigationManager Navigation

private void NavigateToDashboard()
{
    if (UserSession.Role == "Student")
        Navigation.NavigateTo("/studentdashboard", forceLoad: true);
    else if (UserSession.Role == "Professor")
        Navigation.NavigateTo("/professordashboard", forceLoad: true);
    else if (UserSession.Role == "Admin")
        Navigation.NavigateTo("/admindashboard", forceLoad: true);
}
```

**Navigation Features:**
- ✅ **Role-Based Routing**: Automatic redirection based on user role
- ✅ **Force Reload**: `forceLoad: true` ensures fresh page load
- ✅ **Session Validation**: Checks authentication before navigation
- ✅ **Error Handling**: Try-catch blocks for navigation errors

---

## 🎨 UI/UX Design Structure

### Current Implementation Analysis

**✅ Strengths**
- Modern gradient-based design system
- Consistent color scheme (Red theme: #9B1B30)
- Responsive sidebar navigation
- Professional card-based layouts
- Smooth animations and transitions
- Role-specific dashboards
- Interactive hover effects
- Clear visual hierarchy

**🎯 Design Principles Applied**

### 1. Modern Layout Design

**Sidebar Navigation Structure**

```razor
<aside class="sidebar">
    <div class="profile-section">
        <h3>Hello, @displayedUsername!</h3>
        <div class="profile-pic">
            <img src="/images/ENLOGO.png" alt="EN Logo" />
        </div>
        <button class="logout-btn" @onclick="LogoutAsync">Log Out</button>
    </div>
    <nav class="nav-menu">
        <a href="/studentdashboard" class="nav-item active">Dashboard</a>
        <a href="/studentborrow" class="nav-item">Borrow</a>
        <a href="/cart" class="nav-item">Cart</a>
        <a href="/studenthistory" class="nav-item">History</a>
    </nav>
</aside>
```

**Recommended CSS Structure**

```css
.sidebar {
    position: fixed;
    width: 280px;
    height: 100vh;
    background: linear-gradient(180deg, #9B1B30 0%, #6B0F1A 50%, #4A0000 100%);
    color: white;
    box-shadow: 6px 0 32px rgba(0, 0, 0, 0.25);
}

.nav-item {
    padding: 16px 20px;
    border-radius: 10px;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.nav-item:hover {
    background: rgba(255, 255, 255, 0.12);
    padding-left: 28px;
}
```

### 2. Enhanced Form Design

**Modern Input Fields with Validation**

```razor
<div class="form-group">
    <label>Student Name</label>
    <input type="text" value="@studentName" readonly class="readonly-input" />
    <span class="field-hint">Auto-filled from your account</span>
</div>

<div class="professor-selection">
    <label>👨‍🏫 Select Professor for Approval</label>
    <select @bind="selectedProfessorEmail" class="professor-dropdown">
        <option value="">-- Choose a professor --</option>
        @foreach (var prof in allProfessors)
        {
            <option value="@prof.Email">@prof.Name (@prof.Email)</option>
        }
    </select>
</div>
```

**Input Validation States**

```css
.form-input {
    padding: 14px 18px;
    border: 2px solid #dee2e6;
    border-radius: 10px;
    transition: all 0.3s ease;
}

.form-input:focus {
    outline: none;
    border-color: #9B1B30;
    box-shadow: 0 0 0 4px rgba(155, 27, 48, 0.1);
}

.readonly-input {
    background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
    cursor: not-allowed;
}
```

### 3. Interactive Feedback System

**Loading States**

```razor
<button 
    @onclick="SubmitBorrowRequest" 
    class="btn-confirm"
    disabled="@(isSubmitting || string.IsNullOrEmpty(selectedProfessorEmail))">
    @(isSubmitting ? "⏳ SUBMITTING..." : "✅ SUBMIT FOR APPROVAL")
</button>
```

**Status Messages**

```razor
@if (!string.IsNullOrEmpty(message))
{
    <div class="message @(message.Contains("Error") ? "error" : "success")">
        @message
    </div>
}
```

**Notice Section**

```razor
<section class="notice">
    <h3>📢 Notice:</h3>
    <p>@UserDatabase.Notice</p>
</section>
```

### 4. Responsive Design Principles

**Mobile-First Approach**

```css
/* Mobile First (320px+) */
.main-content {
    margin-left: 0;
    padding: 20px;
}

/* Tablet (768px+) */
@media (min-width: 768px) {
    .main-content {
        margin-left: 280px;
        padding: 30px 40px;
    }
}

/* Desktop (1024px+) */
@media (min-width: 1024px) {
    .main-content {
        padding: 40px 60px;
    }
}
```

### 5. Accessibility Enhancements

**ARIA Labels and Screen Reader Support**

```razor
<form role="form" aria-labelledby="borrow-title">
    <h1 id="borrow-title">BORROW REQUEST FORM</h1>
    
    <div class="form-group">
        <label for="professor">Select Professor</label>
        <select 
            id="professor"
            aria-required="true"
            aria-describedby="professor-hint"
            @bind="selectedProfessorEmail">
        </select>
        <span id="professor-hint" class="field-hint">
            Select the professor who will approve your request
        </span>
    </div>
</form>
```

### 6. Advanced Animation and Transitions

**Page Transitions**

```css
.toolroom-card {
    animation: fadeIn 0.5s ease-out;
}

.toolroom-card:nth-child(1) { animation-delay: 0.1s; }
.toolroom-card:nth-child(2) { animation-delay: 0.2s; }
.toolroom-card:nth-child(3) { animation-delay: 0.3s; }
```

**Micro-Interactions**

```css
.btn-confirm {
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.btn-confirm:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(16, 185, 129, 0.4);
}

.btn-confirm:active {
    transform: translateY(0);
}
```

---

## 🚀 Implementation Guide

### Step 1: Enhanced Styling

**Custom CSS Variables for Consistent Theming**

```css
:root {
    --primary-red: #9B1B30;
    --primary-red-dark: #6B0F1A;
    --primary-red-darker: #4A0000;
    --success-green: #10b981;
    --warning-yellow: #fbbf24;
    --error-red: #ef4444;
    --sidebar-width: 280px;
}
```

### Step 2: Form Validation

```csharp
private bool ValidateBorrowRequest()
{
    bool isValid = true;
    
    if (string.IsNullOrWhiteSpace(selectedProfessorEmail))
    {
        message = "Error: Please select a professor to review your request.";
        isValid = false;
    }
    
    if (cartItems == null || !cartItems.Any())
    {
        message = "Error: Your cart is empty.";
        isValid = false;
    }
    
    return isValid;
}
```

### Step 3: State Management

**Session Management**

```csharp
public static class UserSession
{
    private static ConcurrentDictionary<string, SessionData> _sessions = new();
    
    public static string Email
    {
        get => GetSessionValue("Email") ?? string.Empty;
        set => SetSessionValue("Email", value);
    }
    
    public static string Username
    {
        get => GetSessionValue("Username") ?? string.Empty;
        set => SetSessionValue("Username", value);
    }
    
    public static string Role
    {
        get => GetSessionValue("Role") ?? string.Empty;
        set => SetSessionValue("Role", value);
    }
}
```

### Step 4: Security Enhancements

- ✅ **Password Hashing**: BCrypt with salt rounds
- ✅ **Email Verification**: Required for account creation
- ✅ **CSRF Protection**: Built into Blazor Server
- ✅ **Session Management**: Secure session handling
- ✅ **Account Lockout**: Protection against brute force attacks
- ✅ **Input Validation**: Server-side validation for all inputs

---

## 📱 User Experience Flow

### Student Borrowing Journey

```
Login (/) 
    ↓
Student Dashboard (/studentdashboard)
    ↓
Browse Departments (/studentborrow)
    ↓
Select Department (e.g., /electronics)
    ↓
Add Items to Cart
    ↓
Review Cart (/cart)
    ↓
Verify Request (/verifyborrowlist)
    ↓
Submit for Approval
    ↓
Wait for Professor Approval
    ↓
Wait for Admin Processing
    ↓
Items Issued
    ↓
Return Items (via Admin)
```

### Professor Approval Journey

```
Login (/)
    ↓
Professor Dashboard (/professordashboard)
    ↓
View Pending Forms (/professorforms)
    ↓
Review Request Details
    ↓
Approve or Disapprove
    ↓
Form Sent to Admin (if approved)
```

### Administrator Processing Journey

```
Login (/)
    ↓
Admin Dashboard (/admindashboard)
    ↓
View Approved Forms (/adminforms)
    ↓
Verify Inventory Stock
    ↓
Issue Items (/adminissue)
    ↓
Items Borrowed by Student
    ↓
Process Returns (/adminreturns)
    ↓
Update Inventory
```

---

## 🛠️ Technical Implementation

### Enhanced Navigation with State

```csharp
private async Task NavigateWithTransition(string url)
{
    isLoggingOut = true;
    logoutButtonText = "Logging out...";
    StateHasChanged();
    
    await Task.Delay(300);
    
    Navigation.NavigateTo(url, forceLoad: true);
}
```

### Form State Management

```csharp
public class BorrowFormState
{
    public List<CartItem> CartItems { get; set; } = new();
    public string StudentName { get; set; } = string.Empty;
    public string StudentNumber { get; set; } = string.Empty;
    public string SelectedProfessorEmail { get; set; } = string.Empty;
    public bool IsValid => !HasErrors && CartItems.Any();
    public Dictionary<string, string> Errors { get; set; } = new();
    public bool HasErrors => Errors.Any();
}
```

### Business Logic Layer

**Cart Manager**

```csharp
public class CartManager
{
    private readonly AppDbContext _dbContext;
    private readonly IInventoryService _inventoryService;
    
    public async Task<CartSummary> GetCartWithLimitsAsync(string userEmail)
    {
        // Get cart items with inventory limits
        // Validate quantities against max per student
        // Return summary with validation results
    }
}
```

**Borrow Manager**

```csharp
public class BorrowManager
{
    private readonly AppDbContext _dbContext;
    
    public async Task<(bool Success, string ReferenceCode, string Message)> 
        CreateBorrowFormFromCartAsync(
            string studentEmail,
            string studentName,
            string studentNumber,
            string professorEmail)
    {
        // Generate unique reference code
        // Create borrow form
        // Convert cart items to form items
        // Save to database
        // Clear cart
    }
}
```

---

## 🎓 Key Learning Outcomes

### Routing Concepts
- ✅ **Declarative Routing**: Using `@page` directives
- ✅ **Programmatic Navigation**: NavigationManager service
- ✅ **Route Parameters**: Dynamic URL segments
- ✅ **Route Constraints**: Type and pattern matching
- ✅ **Role-Based Routing**: Conditional navigation based on user role

### UI/UX Principles
- ✅ **Progressive Enhancement**: Start basic, enhance gradually
- ✅ **Mobile-First Design**: Design for smallest screen first
- ✅ **Accessibility**: WCAG compliance and screen reader support
- ✅ **Performance**: Minimize layout shifts and optimize animations
- ✅ **Consistent Design System**: Unified color scheme and components

### Modern Web Standards
- ✅ **Semantic HTML**: Proper form structure and ARIA labels
- ✅ **CSS Grid/Flexbox**: Modern layout techniques
- ✅ **CSS Custom Properties**: Maintainable theming system
- ✅ **Component-Based Architecture**: Reusable Razor components
- ✅ **Server-Side Rendering**: Blazor Server for real-time updates

### System Architecture
- ✅ **Repository Pattern**: Data access abstraction
- ✅ **Dependency Injection**: Loose coupling and testability
- ✅ **Business Logic Separation**: Managers for complex operations
- ✅ **Service Layer**: Reusable business services
- ✅ **Entity Framework Core**: ORM for database operations

---

## 🔐 Security Features

### Authentication & Authorization
- **Email Verification**: Required before account activation
- **Password Hashing**: BCrypt with salt rounds
- **Session Management**: Secure session handling
- **Role-Based Access Control**: Different interfaces per role
- **Account Lockout**: Protection against brute force attacks

### Data Protection
- **Input Validation**: Server-side validation for all inputs
- **SQL Injection Prevention**: Parameterized queries via EF Core
- **XSS Protection**: Built into Blazor Server
- **CSRF Protection**: Antiforgery tokens

---

## 📊 System Features

### Inventory Management
- Real-time stock tracking
- Quantity limits per student
- Automatic inventory updates on issue/return
- Department-based organization

### Borrowing Workflow
- Multi-step approval process (Student → Professor → Admin)
- Reference code generation for tracking
- Status tracking throughout the process
- Complete history records

### User Experience
- Modern, responsive design
- Intuitive navigation
- Real-time status updates
- Clear visual feedback
- Accessible interface

---

## 🚀 Getting Started

### Prerequisites
- .NET 9.0 SDK
- SQLite (included with EF Core)
- SMTP server configuration (for email verification)

### Installation
1. Clone the repository
2. Configure `appsettings.json` with database connection string
3. Configure email settings in `EmailService.cs`
4. Run `dotnet restore`
5. Run `dotnet run`

### Database Setup
The database is automatically created on first run with:
- User accounts table
- Inventory items table
- Borrow forms table
- Cart items table
- Verification codes table

---

## 📝 Notes

- The system uses **Blazor Server** for real-time interactivity
- **Entity Framework Core** with SQLite for data persistence
- **Repository Pattern** for data access abstraction
- **Dependency Injection** throughout the application
- **Session-based authentication** with secure session management

---

*This system was developed to modernize and improve the borrowing process for engineering laboratory tools at the University of the East - Caloocan.*
