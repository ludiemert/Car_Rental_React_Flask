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

#### Portugues

# ⚡ Sistema de Aluguel de Carros - React & Flask

Bem-vindo ao repositório do **Sistema de Aluguel de Carros**, um projeto desenvolvido com foco em **tecnologias modernas de frontend e backend**. Este sistema permite a gestão de aluguel e devolução de carros, oferecendo uma interface responsiva e funcional para os usuários.

---

## ✨ **Visão Geral do Projeto**

- **Frontend:** Desenvolvido em **React.js**, com **TailwindCSS** para estilização responsiva.
- **Backend:** API criada com **Flask**, responsável por gerenciar os dados dos carros.
- **Funcionalidades:**
  - Listar carros disponíveis e alugados.
  - Realizar aluguel de carros com datas de retirada e entrega.
  - Calcular valores totais com base nos dias de aluguel.
  - Devolver carros alugados.

---

## 📊 **Tecnologias Utilizadas**

### Frontend:
- **React.js**
- **Axios** (para requisições HTTP)
- **TailwindCSS** (estilização moderna e responsiva)

### Backend:
- **Flask** (framework Python)
- **Flask-CORS** (para permissões de cross-origin)

---

## 🔧 **Como Executar o Projeto**

### **1. Clone o Repositório:**
```bash
https://github.com/seu-usuario/nome-do-repositorio.git
cd nome-do-repositorio
```

### **2. Configuração do Backend (Flask):**

#### Instale as dependências:
```bash
pip install flask flask-cors
```

#### Execute o servidor Flask:
```bash
python app.py
```

O backend estará rodando em: `http://127.0.0.1:5000`

### **3. Configuração do Frontend (React):**

#### Instale as dependências:
```bash
npm install
```

#### Execute o servidor React:
```bash
npm start
```

O frontend estará rodando em: `http://localhost:3000`

---

## 📊 **Arquitetura do Sistema**

### **Backend (Flask):**
O backend gerencia:
- Lista de carros disponíveis.
- Registro de carros alugados.
- APIs para realizar aluguel e devoluções.

#### Endpoints:
- **GET** `/api/carros` - Lista carros disponíveis e alugados.
- **POST** `/api/alugar` - Aluga um carro com base nos dados fornecidos.
- **POST** `/api/devolver` - Devolve um carro alugado.

### **Frontend (React):**
O frontend oferece:
- Uma interface intuitiva para gestão de aluguel e devolução.
- Estilização responsiva usando **TailwindCSS**.
- Integração com o backend via **Axios**.

---

## ✨ **Demonstração Visual**

### **Carros Disponíveis:**
- Lista de todos os carros que podem ser alugados.
- Aluguel realizado com seleção de datas.

### **Carros Alugados:**
- Registro dos carros em uso.
- Opção de devolução.

> **Preview da Interface:**
> Adicione aqui um GIF ou imagem do sistema em funcionamento.

---

## ✨ **Exemplo de Código**

### **Frontend (React):**

#### Função para alugar um carro:
```javascript
const alugarCarro = async (carro, dataRetirada, dataEntrega) => {
  const dataInicio = new Date(dataRetirada);
  const dataFim = new Date(dataEntrega);

  if (dataInicio >= dataFim) {
    alert("A data de retirada deve ser antes da data de entrega!");
    return;
  }

  const diffDays = Math.ceil((dataFim - dataInicio) / (1000 * 60 * 60 * 24));
  const totalPreco = carro.preco * diffDays;

  const confirmacao = window.confirm(
    `Você está alugando o carro "${carro.nome}" por ${diffDays} dias. Total: R$ ${totalPreco}. Deseja continuar?`
  );

  if (!confirmacao) return;

  try {
    const response = await axios.post("http://127.0.0.1:5000/api/alugar", {
      id: carro.id,
      data_retirada: dataRetirada,
      data_entrega: dataEntrega,
      dias: diffDays,
      total_preco: totalPreco,
    });
    alert(response.data.message);
    window.location.reload(); // Atualiza os dados
  } catch (error) {
    console.error("Erro ao alugar o carro:", error);
    alert("Ocorreu um erro ao tentar alugar o carro.");
  }
};
```

### **Backend (Flask):**

#### Endpoint para alugar um carro:
```python
@app.route('/api/alugar', methods=['POST'])
def alugar_carro():
    data = request.json
    carro_id = data['id']
    carro = next(c for c in carros if c["id"] == carro_id)
    carros.remove(carro)
    alugados.append({**carro, **data})
    return jsonify({"message": "Carro alugado com sucesso!"})
```




------


## 🌐 **Contact**


<img align="left" src="https://www.github.com/ludiemert.png?size=150">

#### [**Luciana Diemert**](https://github.com/ludiemert)

🛠 Full-Stack Developer <br>
🖥️ Python Enthusiast | Computer Vision | AI Integrations <br>
📍 São Jose dos Campos – SP, Brazil

<a href="https://www.linkedin.com/in/lucianadiemert" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=flat&logo=linkedin&logoColor=white" alt="LinkedIn Badge" height="25"></a>&nbsp;
<a href="mailto:lucianadiemert@gmail.com" target="_blank"><img src="https://img.shields.io/badge/Gmail-D14836?style=flat&logo=gmail&logoColor=white" alt="Gmail Badge" height="25"></a>&nbsp;
<a href="#"><img src="https://img.shields.io/badge/Discord-%237289DA.svg?logo=discord&logoColor=white" title="LuDiem#0654" alt="Discord Badge" height="25"></a>&nbsp;
<a href="https://www.github.com/ludiemert" target="_blank"><img src="https://img.shields.io/badge/GitHub-100000?style=flat&logo=github&logoColor=white" alt="GitHub Badge" height="25"></a>&nbsp;

<br clear="left"/>

---

Developed with ❤ by [ludiemert](https://github.com/ludiemert).

