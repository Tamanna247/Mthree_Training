PYTHON(WEEK-4,DAY-3)

We started our session with the revision of the Kubernetes script that we had done the previous day and learned a few more things about Minikube, pods, clusters, and cloud terms.

### Kubernetes Concepts

1. **Is Minikube a Kubernetes cluster in the local environment?**
   - Yes, it's a cluster but consists of both master node processes and worker node processes. The main Kubernetes cluster has separate master and worker nodes, which require more resources than a local machine can provide. Minikube allows running Kubernetes locally.

2. **Master Node and Worker Node**
   - **Master Node:**
     - Manages the entire Kubernetes cluster.
     - Decides which worker node runs which pod.
     - Does not serve application requests directly.
   - **Worker Node:**
     - Runs applications inside pods.
     - Handles traffic and processes application requests.
   - **NodePort:**
     - Opens a port on every worker node, allowing external access.
     - Routes requests to the appropriate pod.
     - Runs on worker nodes.
   - **Localhost:**
     - Refers to the master components inside a master node.
     - Refers to a single worker node inside a worker.
     - Cannot be used to access pods from outside the cluster.

3. **What are replicas in Kubernetes? Are they similar to AWS instances?**
   - Yes, but they function within the Kubernetes cluster instead of a cloud provider's infrastructure.
   - The `replicas` field in Kubernetes specifies the number of identical Pod instances running at any time.
   - Kubernetes replicas are used for containerized applications, whereas AWS EC2 instances provide full virtual machines.

4. **Mapping Real-World Scenario to Kubernetes and AWS**
   - **Pod:** One server handling requests (like a single EC2 instance).
   - **Replica:** Multiple servers running the same app (like AWS Auto Scaling).
   - **Cluster:** The infrastructure distributing traffic across multiple pods.
   - **Load Balancer:** Redirects traffic to available pods or instances.

### Object-Oriented Programming (OOP) in Python

- OOP organizes code by treating everything as an object.
- **Example:** A blueprint of a house (Class) vs. an actual house (Object).
- OOP makes code **reusable** and **organized**.
- **Main OOP Concepts:**
  - **Abstraction**
  - **Inheritance**
  - **Encapsulation**
  - **Polymorphism**

#### Class and Object Example
```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age
        self.species = "Canine"
    
    def bark(self):
        return f"{self.name} says Woof!"
    
    def get_info(self):
        return f"{self.name} is {self.age} years old."

fido = Dog("Fido", 3)
bella = Dog("Bella", 5)
print(fido.bark())
print(bella.get_info())
```

### Inheritance in Python
- Similar to a family tree where children inherit properties from parents.
- **Example:**
```python
class Pet:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def speak(self):
        return "Some sound"

class Cat(Pet):
    def __init__(self, name, age, color):
        super().__init__(name, age)
        self.color = color
    
    def speak(self):
        return "Meow"
    
    def purr(self):
        return "Purring..."

whiskers = Cat("Whiskers", 2, "Black")
print(whiskers.speak())  # Outputs: Meow
print(isinstance(whiskers, Pet))  # True
```

### Encapsulation in Python
- Hides unnecessary details and provides only relevant information.
- **Access Modifiers:**
  - **Public:** Accessible from anywhere.
  - **Private:** Accessible only within the class (`__double_underscore`).
  - **Protected:** Accessible within the class and its subclasses (`_single_underscore`).

#### Example:
```python
class BankAccount:
    def __init__(self, owner, balance):
        self.owner = owner  # Public
        self.__balance = balance  # Private
        self._transaction_count = 0  # Protected
    
    def deposit(self, amount):
        self.__balance += amount
        self._transaction_count += 1
    
    def withdraw(self, amount):
        if amount <= self.__balance:
            self.__balance -= amount
            self._transaction_count += 1
    
    def get_balance(self):
        return self.__balance

account = BankAccount("John Doe", 1000)
account.deposit(500)
account.withdraw(200)
print(account.get_balance())  # Outputs: 1300
```

### Afternoon Session
- Brushed up on Kubernetes concepts.
- Practiced Python OOP concepts.
- Discussed doubts in breakout rooms.