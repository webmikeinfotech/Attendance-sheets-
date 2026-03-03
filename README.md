# Attendance-sheets-<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>The Grandmoon Studio</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body {
  margin: 0;
  font-family: 'Segoe UI', sans-serif;
  background: linear-gradient(135deg,#1d2671,#c33764);
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.container {
  background: rgba(255,255,255,0.95);
  padding: 30px;
  width: 95%;
  max-width: 750px;
  border-radius: 15px;
  box-shadow: 0 20px 40px rgba(0,0,0,0.3);
}

h1 {
  text-align: center;
  color: #c3a10b;
  margin-bottom: 5px;
}

.subtitle {
  text-align: center;
  margin-bottom: 25px;
  color: #555;
}

.form-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 15px;
}

.form-group {
  display: flex;
  flex-direction: column;
}

label {
  font-weight: 600;
  margin-bottom: 5px;
}

input, select {
  padding: 10px;
  border-radius: 8px;
  border: 1px solid #ccc;
  font-size: 14px;
}

input:focus, select:focus {
  border-color: #c33764;
  outline: none;
}

.full-width {
  grid-column: span 2;
}

button {
  grid-column: span 2;
  padding: 12px;
  border: none;
  background: linear-gradient(135deg,#1d2671,#c33764);
  color: white;
  font-size: 16px;
  border-radius: 10px;
  cursor: pointer;
  transition: 0.3s;
}

button:hover {
  opacity: 0.9;
  transform: scale(1.02);
}

.success {
  text-align: center;
  margin-top: 15px;
  font-weight: bold;
  color: green;
}

/* Mobile Responsive */
@media(max-width:600px){
  .form-grid{
    grid-template-columns: 1fr;
  }
  .full-width, button{
    grid-column: span 1;
  }
}
</style>
</head>

<body>

<div class="container">
  <h1>The Grandmoon Studio</h1>
  <div class="subtitle">
    Grand WorkDay – Session 2026 <br>
    Wedding Shoot | Jamua, Giridih
  </div>

  <form id="attendencesheet">
    <div class="form-grid">

      <div class="form-group">
        <label>Full Name *</label>
        <input type="text" name="fullName" required>
      </div>

      <div class="form-group">
        <label>Work Type *</label>
        <select name="worktype" required>
          <option value="">Select</option>
          <option>Photography</option>
          <option>Videography</option>
          <option>Cinematography</option>
          <option>Drone Fly</option>
          <option>Assistant</option>
          <option>Other</option>
        </select>
      </div>

      <div class="form-group">
        <label>Events Type *</label>
        <select name="eventstype" required>
          <option value="">Select</option>
          <option>Tilak</option>
          <option>Haldi</option>
          <option>Mehandi/Panneti</option>
          <option>Madwa</option>
          <option>Wedding</option>
          <option>Reception</option>
          <option>Other</option>
        </select>
      </div>

      <div class="form-group">
        <label>Date *</label>
        <input type="date" name="date" required>
      </div>

      <div class="form-group full-width">
        <label>Location *</label>
        <input type="text" name="address" required>
      </div>

      <div class="form-group">
        <label>Camera Model *</label>
        <select name="cameramodel" required>
          <option value="">Select</option>
          <option>Canon M50ii</option>
          <option>Canon 200Dii</option>
          <option>Canon R10</option>
          <option>Canon 80D</option>
          <option>Canon RP</option>
          <option>Nikon Z30</option>
          <option>Nikon Z50</option>
          <option>Nikon Z5ii</option>
          <option>Nikon Z6ii</option>
          <option>Nikon 5600D</option>
          <option>Other</option>
        </select>
      </div>

      <div class="form-group">
        <label>Operator Charge (Optional)</label>
        <input type="number" name="operatorcharge">
      </div>

      <button type="submit">Submit Attendance</button>

    </div>
    <div class="success" id="msg"></div>
  </form>
</div>

<script>
const scriptURL = 'https://script.google.com/macros/s/AKfycbzrC9u2flD_3EDLTJdLGdlf4aK-SBYurUlk7Tg78prWuBnctsL7kutl15eON4S83N1b/exec'
const form = document.getElementById('attendencesheet')

form.addEventListener('submit', e => {
  e.preventDefault()
  fetch(scriptURL, { method: 'POST', body: new FormData(form)})
    .then(response => {
      document.getElementById("msg").innerHTML="Attendance Submitted Successfully ✅"
      form.reset()
    })
    .catch(error => alert("Error! Check Script URL"))
})
</script>

</body>
</html>
