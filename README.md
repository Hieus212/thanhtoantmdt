<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Đăng Ký Dịch Vụ Chăm Sóc Thú Cưng</title>
    <style>
        /* Thiết kế chung cho form */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .form-container {
            background-color: #ffffff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            width: 90%;
            max-width: 600px;
        }

        h1 {
            text-align: center;
            color: #78be20;
        }

        form {
            display: grid;
            grid-template-columns: 1fr 1fr; /* Hai cột */
            gap: 15px;
        }

        label {
            font-weight: bold;
            display: block;
        }

        input, textarea, select {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            margin-bottom: 10px;
            border-radius: 5px;
            border: 1px solid #ccc;
        }

        textarea {
            grid-column: span 2; /* Làm cho textarea chiếm toàn bộ cột */
        }

        input[type="submit"] {
            background-color: #78be20;
            color: white;
            border: none;
            cursor: pointer;
            font-size: 16px;
            padding: 12px 20px;
            grid-column: span 2; /* Làm cho nút submit chiếm toàn bộ cột */
        }

        input[type="submit"]:hover {
            background-color: #658d1b;
        }

        .error {
            color: red;
            font-size: 12px;
        }

        /* Responsive design */
        @media (max-width: 414px) {
            .form-container {
                width: 100%;
            }
            form {
                grid-template-columns: 1fr; /* Chuyển thành một cột cho màn hình nhỏ */
            }
        }

        @media (max-width: 1024px) {
            .form-container {
                width: 80%;
            }
        }

        @media (max-width: 1440px) {
            .form-container {
                width: 60%;
            }
        }
    </style>
</head>
<body>

    <div class="form-container">
        <h1>Đăng Ký Dịch Vụ Chăm Sóc Thú Cưng</h1>
        <form id="pet-care-form" onsubmit="return validateForm()">
            <label for="name">Họ và Tên:</label>
            <input type="text" id="name" name="name" required>
            <div id="name-error" class="error"></div>

            <label for="email">Địa chỉ Email:</label>
            <input type="email" id="email" name="email" required>
            <div id="email-error" class="error"></div>

            <label for="phone">Số điện thoại:</label>
            <input type="text" id="phone" name="phone" required>
            <div id="phone-error" class="error"></div>

            <label for="pet-type">Loại Thú Cưng:</label>
            <select id="pet-type" name="pet-type" required>
                <option value="">Chọn loại thú cưng</option>
                <option value="dog">Chó</option>
                <option value="cat">Mèo</option>
                <option value="other">Khác</option>
            </select>
            <div id="pet-type-error" class="error"></div>

            <label for="description">Mô tả chi tiết nhu cầu:</label>
            <textarea id="description" name="description" rows="4" required></textarea>
            <div id="description-error" class="error"></div>

            <input type="submit" value="Đăng Ký">
        </form>
    </div>

    <script>
        // Function validateForm
        function validateForm() {
            let isValid = true;

            // Reset các lỗi trước
            resetErrors();

            // Kiểm tra họ tên
            const name = document.getElementById("name").value;
            if (name === "") {
                document.getElementById("name-error").innerText = "Họ và tên không được để trống!";
                isValid = false;
            }

            // Kiểm tra email
            const email = document.getElementById("email").value;
            const emailPattern = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/;
            if (!emailPattern.test(email)) {
                document.getElementById("email-error").innerText = "Email không hợp lệ!";
                isValid = false;
            }

            // Kiểm tra số điện thoại
            const phone = document.getElementById("phone").value;
            const phonePattern = /^\d{10,11}$/;
            if (!phonePattern.test(phone)) {
                document.getElementById("phone-error").innerText = "Số điện thoại phải có 10 hoặc 11 chữ số!";
                isValid = false;
            }

            // Kiểm tra loại thú cưng
            const petType = document.getElementById("pet-type").value;
            if (petType === "") {
                document.getElementById("pet-type-error").innerText = "Vui lòng chọn loại thú cưng!";
                isValid = false;
            }

            // Kiểm tra mô tả nhu cầu
            const description = document.getElementById("description").value;
            if (description === "") {
                document.getElementById("description-error").innerText = "Mô tả nhu cầu không được để trống!";
                isValid = false;
            }

            return isValid;
        }

        // Function resetErrors
        function resetErrors() {
            document.getElementById("name-error").innerText = "";
            document.getElementById("email-error").innerText = "";
            document.getElementById("phone-error").innerText = "";
            document.getElementById("pet-type-error").innerText = "";
            document.getElementById("description-error").innerText = "";
        }
    </script>

</body>
</html>
