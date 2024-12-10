<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Đăng Ký Dịch Vụ Chăm Sóc Thú Cưng</title>
    <style>
        /* Định dạng chung */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f7f7f7; /* Nền sáng hơn */
        }

        .container {
            width: 100%;
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        h2 {
            text-align: center;
            color: #4CAF50; /* Xanh lá cây sáng */
        }

        .form-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-size: 14px;
        }

        input[type="text"], input[type="email"], input[type="tel"], select, input[type="submit"] {
            width: 100%;
            padding: 10px;
            font-size: 14px;
            border: 1px solid #ccc;
            border-radius: 5px;
            box-sizing: border-box;
        }

        input[type="submit"] {
            background-color: #FF5733; /* Màu cam nổi bật */
            color: white;
            cursor: pointer;
        }

        input[type="submit"]:hover {
            background-color: #C7461C; /* Màu cam đậm hơn khi hover */
        }

        .error {
            color: red;
            font-size: 12px;
        }

        /* Thiết kế đáp ứng */
        @media (max-width: 414px) {
            .container {
                width: 90%;
                padding: 15px;
            }
        }

        @media (min-width: 415px) and (max-width: 1024px) {
            .container {
                width: 80%;
                padding: 20px;
            }
        }

        @media (min-width: 1025px) {
            .container {
                width: 50%;
                padding: 30px;
            }
        }
    </style>
</head>
<body>

    <div class="container">
        <h2>Đăng Ký Dịch Vụ Chăm Sóc Thú Cưng</h2>
        <form id="registrationForm">
            <div class="form-group">
                <label for="name">Họ và tên:</label>
                <input type="text" id="name" name="name" placeholder="Nhập họ và tên">
                <div id="nameError" class="error"></div>
            </div>

            <div class="form-group">
                <label for="email">Địa chỉ email:</label>
                <input type="email" id="email" name="email" placeholder="Nhập địa chỉ email">
                <div id="emailError" class="error"></div>
            </div>

            <div class="form-group">
                <label for="phone">Số điện thoại:</label>
                <input type="tel" id="phone" name="phone" placeholder="Nhập số điện thoại">
                <div id="phoneError" class="error"></div>
            </div>

            <div class="form-group">
                <label for="pet-type">Loại thú cưng:</label>
                <select id="pet-type" name="pet-type">
                    <option value="">Chọn loại thú cưng</option>
                    <option value="chó">Chó</option>
                    <option value="mèo">Mèo</option>
                    <option value="khác">Khác</option>
                </select>
                <div id="petTypeError" class="error"></div>
            </div>

            <div class="form-group">
                <label for="service">Dịch vụ chăm sóc:</label>
                <select id="service" name="service">
                    <option value="">Chọn dịch vụ chăm sóc</option>
                    <option value="tắm">Tắm cho thú cưng</option>
                    <option value="cắt lông">Cắt lông cho thú cưng</option>
                    <option value="chăm sóc sức khỏe">Chăm sóc sức khỏe</option>
                    <option value="vệ sinh miệng">Vệ sinh miệng cho thú cưng</option>
                </select>
                <div id="serviceError" class="error"></div>
            </div>

            <div class="form-group">
                <label for="time">Thời gian chăm sóc:</label>
                <input type="text" id="time" name="time" placeholder="Nhập thời gian chăm sóc">
                <div id="timeError" class="error"></div>
            </div>

            <div class="form-group">
                <input type="submit" value="Đăng ký">
            </div>
        </form>
    </div>

    <script>
        document.getElementById('registrationForm').addEventListener('submit', function(event) {
            event.preventDefault();  // Ngừng gửi form nếu có lỗi

            // Xóa các lỗi cũ
            document.getElementById('nameError').innerText = '';
            document.getElementById('emailError').innerText = '';
            document.getElementById('phoneError').innerText = '';
            document.getElementById('petTypeError').innerText = '';
            document.getElementById('serviceError').innerText = '';
            document.getElementById('timeError').innerText = '';

            let isValid = true;

            // Kiểm tra họ và tên
            const name = document.getElementById('name').value;
            if (name === '') {
                document.getElementById('nameError').innerText = 'Vui lòng nhập họ và tên.';
                isValid = false;
            }

            // Kiểm tra email
            const email = document.getElementById('email').value;
            const emailRegex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$/;
            if (email === '') {
                document.getElementById('emailError').innerText = 'Vui lòng nhập địa chỉ email.';
                isValid = false;
            } else if (!emailRegex.test(email)) {
                document.getElementById('emailError').innerText = 'Địa chỉ email không hợp lệ.';
                isValid = false;
            }

            // Kiểm tra số điện thoại
            const phone = document.getElementById('phone').value;
            const phoneRegex = /^\d{10}$/;
            if (phone === '') {
                document.getElementById('phoneError').innerText = 'Vui lòng nhập số điện thoại.';
                isValid = false;
            } else if (!phoneRegex.test(phone)) {
                document.getElementById('phoneError').innerText = 'Số điện thoại không hợp lệ.';
                isValid = false;
            }

            // Kiểm tra loại thú cưng
            const petType = document.getElementById('pet-type').value;
            if (petType === '') {
                document.getElementById('petTypeError').innerText = 'Vui lòng chọn loại thú cưng.';
                isValid = false;
            }

            // Kiểm tra dịch vụ chăm sóc
            const service = document.getElementById('service').value;
            if (service === '') {
                document.getElementById('serviceError').innerText = 'Vui lòng chọn dịch vụ chăm sóc.';
                isValid = false;
            }

            // Kiểm tra thời gian chăm sóc
            const time = document.getElementById('time').value;
            if (time === '') {
                document.getElementById('timeError').innerText = 'Vui lòng nhập thời gian chăm sóc.';
                isValid = false;
            }

            if (isValid) {
                alert('Đăng ký thành công!');
                // Gửi form hoặc xử lý tiếp theo tại đây
            }
        });
    </script>

</body>
</html>
