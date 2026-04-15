[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23573937&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 26ai.hieudm@vinuni.edu.vn
**Name:** Do Minh Hieu
---

## Mo ta

Day 10 lab yeu cau xay dung ETL pipeline co kha nang quan sat du lieu (data observability).
Trong bai lam nay, minh da hoan thien day du 4 buoc:

- Extract: Doc du lieu tu file `raw_data.json`.
- Validate: Loai bo record loi (price <= 0, category rong).
- Transform: Tinh `discounted_price = price * 0.9`, chuan hoa `category` ve Title Case, them timestamp `processed_at`.
- Load: Luu du lieu da xu ly ra `processed_data.csv`.

Ngoai ra, pipeline co logging de hien thi tong so record hop le va so record bi loai, phuc vu kiem soat chat luong du lieu.

---

## Cach chay (How to Run)

### Prerequisites
```bash
python3 -m pip install pandas pytest
```

### Chay ETL Pipeline
```bash
python3 solution.py
```

Ket qua sau khi chay:
- Tao file `processed_data.csv`.
- In ra thong tin validation (valid records va errors dropped).

### Chay test tu dong (goi y)
```bash
# Chay tu thu muc goc cua project (data-pipeline-observability-HIEU-ntp)
python3 -m pytest tests/test_autograder.py -q

# Neu dang o trong thu muc tests thi dung:
python3 -m pytest test_autograder.py -q
```

### Chay Agent Simulation (Stress Test)
```bash
# Tao bo du lieu rac
python3 generate_garbage.py

# Chay mo phong agent voi clean data va garbage data
python3 agent_simulation.py
```

---

## Cau truc thu muc

```
├── solution.py              # Script ETL chinh
├── raw_data.json            # Du lieu dau vao
├── processed_data.csv       # Du lieu dau ra sau ETL
├── generate_garbage.py      # Tao du lieu rac de stress test
├── agent_simulation.py      # Mo phong agent tra loi dua tren du lieu
├── experiment_report.md     # Bao cao so sanh Clean vs Garbage
├── tests/test_autograder.py # Bo test cham diem tu dong
└── README.md                # Tai lieu huong dan
```

---

## Ket qua

Voi du lieu mau hien tai trong `raw_data.json`:

- Tong records extract: 5
- Records hop le sau validate: 3
- Records bi loai: 2
- Output duoc luu thanh cong vao `processed_data.csv`

Pipeline dap ung cac tieu chi chinh cua lab:
- Co validation logic cho quality checks.
- Co business transformation ro rang.
- Co timestamp de theo doi qua trinh xu ly.
- Co logging de quan sat so luong records duoc giu/loai.
