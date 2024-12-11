# Car_Rental_React_Flask
Frontend: **React.js** and styled with **TailwindCSS** for responsive design. - **Backend:** API created using **Flask**, responsible for managing car data.

# ⚡ Car Rental System - React & Flask

Welcome to the **Car Rental System** repository, a project developed with a focus on **modern frontend and backend technologies**. This system facilitates car rentals and returns, providing users with a responsive and functional interface.

---

## ✨ **Project Overview**

- **Frontend:** Built with **React.js** and styled with **TailwindCSS** for responsive design.
- **Backend:** API created using **Flask**, responsible for managing car data.
- **Features:**
  - List available and rented cars.
  - Rent cars with pickup and return dates.
  - Calculate total prices based on rental days.
  - Return rented cars.

---

## 📊 **Technologies Used**

### Frontend:
- **React.js**
- **Axios** (for HTTP requests)
- **TailwindCSS** (modern and responsive styling)

### Backend:
- **Flask** (Python framework)
- **Flask-CORS** (for cross-origin permissions)

---

## 🔧 **How to Run the Project**

### **1. Clone the Repository:**
```bash
https://github.com/your-username/repository-name.git
cd repository-name
```

### **2. Backend Setup (Flask):**

#### Install dependencies:
```bash
pip install flask flask-cors
```

#### Run the Flask server:
```bash
python app.py
```

The backend will be running at: `http://127.0.0.1:5000`

### **3. Frontend Setup (React):**

#### Install dependencies:
```bash
npm install
```

#### Run the React server:
```bash
npm start
```

The frontend will be running at: `http://localhost:3000`

---

## 📊 **System Architecture**

### **Backend (Flask):**
The backend handles:
- List of available cars.
- Record of rented cars.
- APIs for rentals and returns.

#### Endpoints:
- **GET** `/api/cars` - Lists available and rented cars.
- **POST** `/api/rent` - Rents a car based on provided data.
- **POST** `/api/return` - Returns a rented car.

### **Frontend (React):**
The frontend provides:
- An intuitive interface for managing rentals and returns.
- Responsive styling using **TailwindCSS**.
- Backend integration via **Axios**.

---

## ✨ **Visual Demo**

### **Available Cars:**
- Displays all cars available for rental.
- Rentals completed with date selection.

### **Rented Cars:**
- Records of cars currently rented.
- Return option available.

> **Interface Preview:**
> Add a GIF or image showcasing the system in action here.

---

## ✨ **Code Example**

### **Frontend (React):**

#### Function to rent a car:
```javascript
const rentCar = async (car, pickupDate, returnDate) => {
  const startDate = new Date(pickupDate);
  const endDate = new Date(returnDate);

  if (startDate >= endDate) {
    alert("Pickup date must be before the return date!");
    return;
  }

  const diffDays = Math.ceil((endDate - startDate) / (1000 * 60 * 60 * 24));
  const totalPrice = car.price * diffDays;

  const confirmation = window.confirm(
    `You are renting the car "${car.name}" for ${diffDays} days. Total: $${totalPrice}. Proceed?`
  );

  if (!confirmation) return;

  try {
    const response = await axios.post("http://127.0.0.1:5000/api/rent", {
      id: car.id,
      pickup_date: pickupDate,
      return_date: returnDate,
      days: diffDays,
      total_price: totalPrice,
    });
    alert(response.data.message);
    window.location.reload(); // Refresh data
  } catch (error) {
    console.error("Error renting the car:", error);
    alert("An error occurred while trying to rent the car.");
  }
};
```

### **Backend (Flask):**

#### Endpoint to rent a car:
```python
@app.route('/api/rent', methods=['POST'])
def rent_car():
    data = request.json
    car_id = data['id']
    car = next(c for c in cars if c["id"] == car_id)
    cars.remove(car)
    rented.append({**car, **data})
    return jsonify({"message": "Car successfully rented!"})
```

---

## 🎨 **Contributions**
Contributions are welcome! Feel free to open an **issue** or submit a **pull request** with improvements.

---

## 🌐 **Contact**

For questions or suggestions, get in touch:

- **Email:** youremail@example.com
- **LinkedIn:** [Your LinkedIn](https://linkedin.com/in/your-profile)

---

Developed with ❤ by [Your Name](https://github.com/your-username).

