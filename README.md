<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Đăng Ký Cầu Lông Cuối Tuần</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        body { 
            font-family: 'Plus Jakarta Sans', sans-serif; 
            background: #0f172a; 
            background-image: 
                radial-gradient(at 0% 0%, rgba(34, 197, 94, 0.15) 0px, transparent 50%),
                radial-gradient(at 100% 100%, rgba(59, 130, 246, 0.15) 0px, transparent 50%);
            min-height: 100vh; 
            color: #f8fafc;
        }
        .card-custom { 
            background: rgba(30, 41, 59, 0.7); 
            backdrop-filter: blur(20px); 
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 2rem; 
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
        }
        .countdown-box {
            background: linear-gradient(145deg, #1e293b, #334155);
            border: 1px solid rgba(255, 255, 255, 0.05);
            border-radius: 1.25rem;
        }
        .input-style {
            background: rgba(15, 23, 42, 0.6);
            border: 1px solid rgba(255, 255, 255, 0.1);
            color: white;
            transition: all 0.3s ease;
        }
        .input-style:focus {
            border-color: #22c55e;
            box-shadow: 0 0 0 4px rgba(34, 197, 94, 0.2);
            background: rgba(15, 23, 42, 0.8);
        }
        .btn-playful {
            background: linear-gradient(90deg, #22c55e, #3b82f6);
            box-shadow: 0 10px 15px -3px rgba(34, 197, 94, 0.4);
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .btn-playful:hover:not(:disabled) {
            transform: translateY(-2px);
            filter: brightness(1.1);
        }
        .btn-playful:disabled {
            background: #475569;
            box-shadow: none;
            cursor: not-allowed;
            opacity: 0.6;
        }
        .status-badge {
            padding: 4px 12px;
            border-radius: 9999px;
            font-size: 0.75rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }
        .badge-open { background: rgba(34, 197, 94, 0.2); color: #4ade80; border: 1px solid rgba(34, 197, 94, 0.3); }
        .badge-closed { background: rgba(239, 68, 68, 0.2); color: #f87171; border: 1px solid rgba(239, 68, 68, 0.3); }
        
        .floating { animation: float 3s ease-in-out infinite; }
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }
    </style>
</head>
<body class="p-4 md:p-12 flex items-center justify-center">
    <div class="max-w-xl w-full card-custom p-8 md:p-12">
        <div class="flex justify-center mb-4" id="statusBadgeContainer"></div>

        <header class="text-center mb-10">
            <h1 class="text-4xl font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-green-400 to-blue-400 mb-3 leading-tight">
                Sân Cầu Cuối Tuần 🏸
            </h1>
            <p id="subHeader" class="text-slate-400 text-sm">Đăng ký tham gia giao lưu cùng anh em.</p>
        </header>

        <div class="mb-12">
            <div class="flex justify-center gap-3 sm:gap-4" id="countdown">
                <div class="countdown-box p-3 sm:p-4 w-24 text-center">
                    <span id="matchDate" class="text-xl sm:text-2xl font-black text-green-400 block floating">--/--</span>
                    <p class="text-[10px] text-slate-500 font-bold uppercase tracking-tighter">Ngày Đánh</p>
                </div>
                <div class="countdown-box p-3 sm:p-4 w-24 text-center">
                    <span id="timeLeft" class="text-xl sm:text-2xl font-black text-blue-400 block floating" style="animation-delay: 0.5s">--</span>
                    <p id="timeLeftLabel" class="text-[10px] text-slate-500 font-bold uppercase tracking-tighter">Hạn Còn</p>
                </div>
            </div>
        </div>

        <form id="registrationForm" class="space-y-6">
            <div class="group">
                <label class="block text-xs font-bold text-slate-400 uppercase tracking-widest mb-2 ml-1">Họ và Tên</label>
                <input type="text" name="FullName" required 
                       class="w-full px-5 py-4 input-style rounded-2xl outline-none text-base font-medium"
                       placeholder="Nhập tên của bạn...">
            </div>

            <div class="grid grid-cols-2 gap-4">
                <label class="relative flex items-center justify-center p-4 input-style rounded-2xl cursor-pointer group has-[:checked]:border-green-500 has-[:checked]:bg-green-500/10">
                    <input type="radio" name="Gender" value="Nam" checked class="sr-only">
                    <span class="text-sm font-bold text-slate-300 group-has-[:checked]:text-green-400">🕺 Nam</span>
                </label>
                <label class="relative flex items-center justify-center p-4 input-style rounded-2xl cursor-pointer group has-[:checked]:border-blue-500 has-[:checked]:bg-blue-500/10">
                    <input type="radio" name="Gender" value="Nữ" class="sr-only">
                    <span class="text-sm font-bold text-slate-300 group-has-[:checked]:text-blue-400">💃 Nữ</span>
                </label>
            </div>

            <div>
                <label class="block text-xs font-bold text-slate-400 uppercase tracking-widest mb-2 ml-1">Trạng thái tham gia</label>
                <select name="Status" id="statusSelect" required
                        class="w-full px-5 py-4 input-style rounded-2xl outline-none text-base font-medium appearance-none cursor-pointer">
                    <option value="Yes">🏸 Có mặt, chiến thôi!</option>
                    <option value="No">🏠 Vắng, hẹn tuần sau</option>
                </select>
            </div>

            <input type="hidden" name="MatchDate" id="hiddenMatchDate">

            <div class="pt-4">
                <button type="submit" id="submitBtn"
                        class="w-full btn-playful text-white font-black py-5 rounded-2xl shadow-lg tracking-widest uppercase text-sm">
                    XÁC NHẬN ĐI ĐÁNH 🏸
                </button>
            </div>
            
            <p id="message" class="text-center text-sm font-bold mt-4 px-4 py-2 rounded-xl hidden"></p>
        </form>
    </div>

    <script>
        // QUAN TRỌNG: Hãy dán link Web App URL của bạn vào đây
        const scriptURL = 'https://script.google.com/macros/s/AKfycbzsC7LHERwtbcEMxConyo-Yc6cL7aWptCkeiQz9xIQCtRHl18iyTOyxBK1rfp6sFSyN/exec'; 
        
        function updateLogic() {
            const now = new Date();
            const currentDay = now.getDay(); // 0: CN, 1: T2, ..., 6: T7
            
            // Tính ngày Thứ 7 của tuần này
            const daysUntilSaturday = 6 - (currentDay === 0 ? 7 : currentDay);
            const saturday = new Date(now);
            saturday.setDate(now.getDate() + (currentDay === 0 ? -1 : daysUntilSaturday));
            
            const dateStr = saturday.toLocaleDateString('vi-VN', { day: '2-digit', month: '2-digit' });
            document.getElementById('matchDate').innerText = dateStr;
            document.getElementById('hiddenMatchDate').value = saturday.toDateString();

            const badgeContainer = document.getElementById('statusBadgeContainer');
            const submitBtn = document.getElementById('submitBtn');
            const subHeader = document.getElementById('subHeader');
            const timeLeft = document.getElementById('timeLeft');
            const timeLeftLabel = document.getElementById('timeLeftLabel');

            // Mở từ T2 (1) đến T5 (4)
            const isOpen = (currentDay >= 1 && currentDay <= 4);

            if (isOpen) {
                badgeContainer.innerHTML = `<span class="status-badge badge-open">Đang mở đăng ký 🟢</span>`;
                submitBtn.disabled = false;
                subHeader.innerText = "Hạn chốt vào Thứ 5 hàng tuần.";
                const daysLeft = 4 - currentDay;
                timeLeft.innerText = daysLeft > 0 ? `${daysLeft} Ngày` : "Hôm nay";
                timeLeftLabel.innerText = "Hạn Còn";
            } else {
                badgeContainer.innerHTML = `<span class="status-badge badge-closed">Đã đóng đăng ký 🔴</span>`;
                submitBtn.disabled = true;
                submitBtn.innerText = "HẾT HẠN ĐĂNG KÝ";
                timeLeft.innerText = "Đã Chốt";
                timeLeftLabel.innerText = "Trạng Thái";
                subHeader.innerText = (currentDay === 5 || currentDay === 6) ? "Hẹn gặp bạn ở sân!" : "Mở lại vào Thứ 2 tuần sau.";
            }
        }

        updateLogic();

        const form = document.getElementById('registrationForm');
        const message = document.getElementById('message');
        const submitBtn = document.getElementById('submitBtn');

        form.addEventListener('submit', e => {
            e.preventDefault();
            message.classList.add('hidden');

            if (!scriptURL || scriptURL.includes('YOUR_GOOGLE')) {
                message.innerText = "⚠️ Lỗi: Chưa có link Script URL!";
                message.className = "text-center text-sm font-bold text-yellow-400 block bg-yellow-400/10 mt-4 px-4 py-2 rounded-xl";
                return;
            }

            submitBtn.disabled = true;
            submitBtn.innerText = "ĐANG GỬI...";
            message.className = "text-center text-sm font-bold text-indigo-400 block bg-indigo-400/10 animate-pulse mt-4 px-4 py-2 rounded-xl";
            message.innerText = "Đang ghi danh vào danh sách... 🏸";

            fetch(scriptURL, { method: 'POST', body: new FormData(form)})
            .then(response => {
                message.innerText = "XONG! Chúc bạn có buổi đánh vui vẻ ✨";
                message.className = "text-center text-sm font-bold text-green-400 block bg-green-400/10 mt-4 px-4 py-2 rounded-xl";
                form.reset();
                submitBtn.disabled = false;
                submitBtn.innerText = "XÁC NHẬN ĐI ĐÁNH 🏸";
                setTimeout(() => message.classList.add('hidden'), 5000);
            })
            .catch(error => {
                message.innerText = "Lỗi kết nối! Vui lòng thử lại.";
                message.className = "text-center text-sm font-bold text-red-400 block bg-red-400/10 mt-4 px-4 py-2 rounded-xl";
                submitBtn.disabled = false;
                submitBtn.innerText = "XÁC NHẬN ĐI ĐÁNH 🏸";
            });
        });
    </script>
</body>
</html># DKcaulong
