# html-form-student-record-js-validation-
. Design HTML form for keeping student record, apply JavaScript validation for restriction of 
mandatory fields, numeric field, email-address field, specific value in a field etc. 
CODE
 <!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Student Record Form</title>
   
    <script>
        function validateForm() {
            let valid = true;

            // Clear previous error messages
            document.querySelectorAll('.error').forEach(function(element) {
                element.innerText = '';
            });

            // Validate Name (mandatory)
            let name = document.getElementById('name').value;
            if (name === '') {
                document.getElementById('nameError').innerText = 'Name is required.';
                valid = false;
            }

            // Validate Age (numeric)
            let age = document.getElementById('age').value;
            if (age === '' || isNaN(age) || age <= 0) {
                document.getElementById('ageError').innerText = 'Please enter a valid age.';
                valid = false;
            }

            // Validate Email (format)
            let email = document.getElementById('email').value;
            let emailPattern = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
            if (!emailPattern.test(email)) {
                document.getElementById('emailError').innerText = 'Please enter a valid email address.';
                valid = false;
            }

            // Validate Course (specific value)
            let course = document.getElementById('course').value;
            if (course === '') {
                document.getElementById('courseError').innerText = 'Please select a course.';
                valid = false;
            }

            return valid;
        }
    </script>
</head>
<body>
    <div class="container">
        <h2>Student Record Form</h2>
        <form onsubmit="return validateForm()">
            <div class="form-group">
                <label for="name">Name:</label>
                <input type="text" id="name" name="name">
                <div id="nameError" class="error"></div>
            </div>
            <div class="form-group">
                <label for="age">Age:</label>
                <input type="number" id="age" name="age">
                <div id="ageError" class="error"></div>
            </div>
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" id="email" name="email">
                <div id="emailError" class="error"></div>
            </div>
            <div class="form-group">
                <label for="course">Course:</label>
                <select id="course" name="course">
                    <option value="">Select a course</option>
                    <option value="computer science">computer science</option>
                    <option value="philosophy">philosophy</option>
                    <option value="software development">software development</option>
                    <option value="bcom">bcom</option>
                    <option value="psychology">psychology</option>
                </select>
                <div id="courseError" class="error"></div>
            </div>
            <div class="form-buttons">
                <button type="submit">Submit</button>
                <button type="reset" class="reset">Reset</button>
            </div>
        </form>
    </div>
</body>
</html>
