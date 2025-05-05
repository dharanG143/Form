<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Customer Form</title>

  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>

  <!-- Bootstrap CSS -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body class="bg-gray-100 py-5">

  <div class="max-w-2xl mx-auto bg-white p-6 rounded-lg shadow-lg">
    <h2 class="text-2xl font-bold text-center mb-6">Customer Form</h2>

    <form id="customerForm" novalidate>

      <!-- Name -->
      <div class="mb-3">
        <label class="form-label">Name</label>
        <input type="text" id="name" class="form-control" required>
        <small class="text-danger d-none" id="nameError">Name must be more than 3 letters and no numbers.</small>
      </div>

      <!-- Date of Birth -->
      <div class="mb-3">
        <label class="form-label">Date of Birth</label>
        <input type="date" id="dob" class="form-control" required>
        <small class="text-danger d-none" id="dobError">Please select your date of birth.</small>
      </div>

      <!-- Gender -->
      <div class="mb-3">
        <label class="form-label">Gender</label>
        <select id="gender" class="form-select" required>
          <option value="">Select Gender</option>
          <option>Male</option>
          <option>Female</option>
          <option>Others</option>
        </select>
        <small class="text-danger d-none" id="genderError">Please select a gender.</small>
      </div>

      <!-- Email -->
      <div class="mb-3">
        <label class="form-label">Email</label>
        <input type="email" id="email" class="form-control" required>
        <small class="text-danger d-none" id="emailError">Please enter a valid email.</small>
      </div>

      <!-- Mobile Number -->
      <div class="mb-3">
        <label class="form-label">Mobile Number</label>
        <input type="tel" id="mobile" class="form-control" required>
        <small class="text-danger d-none" id="mobileError">Mobile number must be 10 digits.</small>
      </div>

      <!-- WhatsApp Number -->
      <div class="mb-3">
        <label class="form-label">WhatsApp Number <small>(optional)</small></label>
        <input type="tel" id="whatsapp" class="form-control">
        <small class="text-danger d-none" id="whatsappError">WhatsApp number must be 10 digits.</small>
      </div>

      <!-- Address -->
      <div class="mb-3">
        <label class="form-label">Address</label>
        <textarea id="address" class="form-control" required></textarea>
        <small class="text-danger d-none" id="addressError">Please enter your address.</small>
      </div>

      <!-- City -->
      <div class="mb-3">
        <label class="form-label">City</label>
        <select id="city" class="form-select" required>
          <option value="">Select City</option>
          <option>Trichy</option>
          <option>Chennai</option>
          <option>Madurai</option>
        </select>
        <small class="text-danger d-none" id="cityError">Please select your city.</small>
      </div>

      <!-- Pincode -->
      <div class="mb-3">
        <label class="form-label">Pincode</label>
        <input type="text" id="pincode" class="form-control" required>
        <small class="text-danger d-none" id="pincodeError">Pincode must be exactly 6 digits.</small>
      </div>

      <!-- Password -->
      <div class="mb-3">
        <label class="form-label">Password</label>
        <input type="password" id="password" class="form-control" required>
        <small class="text-danger d-none" id="passwordError">Password is required (min 6 characters).</small>
      </div>

      <!-- Image Upload -->
      <div class="mb-3">
        <label class="form-label">Upload Image</label>
        <input type="file" id="image" class="form-control" accept=".png,.PNG,.jpg,.JPG" required>
        <small class="text-danger d-none" id="imageError">Only .png, .PNG, .jpg, .JPG files allowed.</small>
      </div>

      <!-- Buttons -->
      <div >
        <button type="submit" class="btn btn-primary">Register</button>
        <a href="#" class="btn btn-outline-secondary ">Login</a>
      </div>
    </form>
  </div>

  <!-- JavaScript Validation -->
  <!-- Inside the <script> tag at the bottom of your HTML -->
<script>
    document.getElementById("customerForm").addEventListener("submit", function (e) {
      e.preventDefault();
  
      let valid = true;
  
      // Name
      const name = document.getElementById("name").value;
      const nameError = document.getElementById("nameError");
      const nameValid = /^[A-Za-z\s]{4,}$/.test(name);
      nameError.classList.toggle("d-none", nameValid);
      if (!nameValid) valid = false;
  
      // DOB
      const dob = document.getElementById("dob").value;
      const dobError = document.getElementById("dobError");
      dobError.classList.toggle("d-none", dob !== "");
      if (!dob) valid = false;
  
      // Gender
      const gender = document.getElementById("gender").value;
      const genderError = document.getElementById("genderError");
      genderError.classList.toggle("d-none", gender !== "");
      if (!gender) valid = false;
  
      // Email
      const email = document.getElementById("email").value;
      const emailError = document.getElementById("emailError");
      const emailValid = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
      emailError.classList.toggle("d-none", emailValid);
      if (!emailValid) valid = false;
  
      // Mobile
      const mobile = document.getElementById("mobile").value;
      const mobileError = document.getElementById("mobileError");
      const mobileValid = /^[0-9]{10}$/.test(mobile);
      mobileError.classList.toggle("d-none", mobileValid);
      if (!mobileValid) valid = false;
  
      // WhatsApp
      const whatsapp = document.getElementById("whatsapp").value;
      const whatsappError = document.getElementById("whatsappError");
      const whatsappValid = whatsapp === "" || /^[0-9]{10}$/.test(whatsapp);
      whatsappError.classList.toggle("d-none", whatsappValid);
      if (!whatsappValid) valid = false;
  
      // Address
      const address = document.getElementById("address").value;
      const addressError = document.getElementById("addressError");
      addressError.classList.toggle("d-none", address.trim() !== "");
      if (address.trim() === "") valid = false;
  
      // City
      const city = document.getElementById("city").value;
      const cityError = document.getElementById("cityError");
      cityError.classList.toggle("d-none", city !== "");
      if (!city) valid = false;
  
      // Pincode
      const pincode = document.getElementById("pincode").value;
      const pincodeError = document.getElementById("pincodeError");
      const pincodeValid = /^[0-9]{6}$/.test(pincode);
      pincodeError.classList.toggle("d-none", pincodeValid);
      if (!pincodeValid) valid = false;
  
      // Password
      const password = document.getElementById("password").value;
      const passwordError = document.getElementById("passwordError");
      const passwordValid = password.length >= 6;
      passwordError.classList.toggle("d-none", passwordValid);
      if (!passwordValid) valid = false;
  
      // Image
      const image = document.getElementById("image").files[0];
      const imageError = document.getElementById("imageError");
      const allowedExtensions = /(\.jpg|\.JPG|\.png|\.PNG)$/;
      const imageValid = image && allowedExtensions.test(image.name);
      imageError.classList.toggle("d-none", imageValid);
      if (!imageValid) valid = false;
  
      if (valid) {
        // You can uncomment the next line to actually submit via JS or backend.
        // this.submit(); or send data to backend here
        console.log("Form submitted successfully.");
      }
    });
  </script>
  
  
</body>
</html>

