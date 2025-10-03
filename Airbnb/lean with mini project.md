# 🏡 Airbnb Clone with Project-Based Learning

### 🔹 Step 1: Hello World (Spring Boot Basics)

* Create a Spring Boot project with `Spring Web` dependency.
* Add one `Controller` → return `index.html` with a message.
* ✅ You learn: `@SpringBootApplication`, `@Controller`, `@GetMapping`.

---

### 🔹 Step 2: Property Listings (Spring MVC + Thymeleaf)

* Create a `Property` class (title, location, price).
* Hardcode a few properties in a list and show them on `listings.html`.
* ✅ You learn: Passing data from Controller → View with `Model`.

---

### 🔹 Step 3: Database Connection (Spring Data JPA)

* Connect to MySQL in `application.properties`.
* Create `Property` entity + `PropertyRepository`.
* Show all properties from database on `listings.html`.
* ✅ You learn: `@Entity`, `JpaRepository`, Database integration.

---

### 🔹 Step 4: Property Details Page

* When you click a property, open `/property/{id}`.
* Fetch property by ID from DB.
* ✅ You learn: `@PathVariable`, fetching single records.

---

### 🔹 Step 5: User Authentication (Spring Security)

* Create `User` entity + `UserRepository`.
* Add `/register` & `/login` pages.
* Secure booking so only logged-in users can book.
* ✅ You learn: Spring Security, `UserDetailsService`.

---

### 🔹 Step 6: Booking System

* Create `Booking` entity (user, property, check_in, check_out).
* On property page → Book Now → save booking in DB.
* ✅ You learn: `@ManyToOne` relationships, form handling.

---

### 🔹 Step 7: User Profile

* Show logged-in user’s bookings in `/profile`.
* ✅ You learn: Session, fetching user-specific data.

---

### 🔹 Step 8: Admin Panel (Optional, but good for college project)

* Admin can add/edit/delete properties.
* ✅ You learn: Role-based access control.

---

# 📂 Learning by Doing → Flow

1. Start simple → Homepage with properties.
2. Slowly add database.
3. Then add login/register.
4. Then booking system.
5. Finally profile + admin.

By the end, you’ll have a **working Airbnb clone** AND you’ll have learned all the **Spring Boot core concepts** 🎉.

---
