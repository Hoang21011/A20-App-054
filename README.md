
# Lý do chọn đề tài  
## “Kiểm thử UI tự động & QA phần mềm – xây dựng Screen & UI Agent”

---

## 1. Nhu cầu thị trường cao
- Công ty phần mềm luôn cần QA Automation để giảm chi phí test manual  
- Thiếu nhân lực QA automation chất lượng → dễ xin job / freelance  
- Có thể làm dịch vụ:
  - Viết automation test cho startup
  - Audit chất lượng sản phẩm
  - Build test pipeline cho doanh nghiệp

---

## 2. Giải quyết bài toán thực tế
- Test manual:
  - Tốn thời gian, dễ sai sót
  - Không scale khi hệ thống lớn
- UI Agent giúp:
  - Tự động test theo flow người dùng
  - Phát hiện bug sớm
  - Chạy regression nhanh

---
# So sánh Playwright, Selenium, Cypress

## 1. Playwright
- Modern, nhanh, auto-wait
- Hỗ trợ nhiều browser (Chromium, Firefox, WebKit)
- Có sẵn test runner + report

## 2. Selenium
- Industry standard, đa ngôn ngữ
- Setup phức tạp
- Dễ flaky (không auto-wait)

## 3. Cypress
- Dễ học, debug tốt
- Setup nhanh
- Hạn chế browser, không hỗ trợ multi-tab tốt

---

## Lựa chọn cho project

**Vậy nên, trong project này Playwright được sử dụng vì:**
- Dễ học và mạnh
- Ít lỗi vặt
- Phù hợp cả demo và production

---
# Architecture 

---

##  1. Input Layer

### **Input URL, DOM (Document Object Model), Screenshot**
- URL của hệ thống cần test (web app)
- Là entry point cho toàn bộ pipeline

---

## Test Generation

### **Test Generator (LLM)**
- Phân tích UI/flow từ URL
- Sinh test cases (Gherkin / code)
- Output:
  - Test cases có cấu trúc
  - 
## 3. Test Execution

### **Test Executor (Playwright)**
- Dùng :contentReference[oaicite:1]{index=1} để:
  - Chạy test cases
  - Tương tác UI (click, input, navigation)

### Output:
- Logs
- Screenshots
- Videos

---

## 4. Bug Analysis

### **Bug Analyzer (LLM)**
- Nhận:
  - Logs + screenshot + video
- Phân tích:
  - Test fail ở đâu
  - Root cause (UI, timing, locator…)

### Output:
- Bug description
- Severity

---

## 5. Reporting

### **Report Generator**
- Tổng hợp:
  - Test results
  - Bug analysis
- Xuất:
  - HTML / PDF / JSON

---

#  6. Core Agent Modules

## 6.1 Test Generation & QA Module

### **Test Case Generator (LLM)**
- Sinh test case

### **Config & Data Manager**
- Quản lý:
  - Test data
  - Config (env, base URL…)

---

## 6.2 Test Execution & UI Module

### **Test Runner / Executor**
- Điều phối việc chạy test

### **UI Automation Engine (Playwright wrapper)**
- Wrapper quanh Playwright:
  - Abstract action (click, fill…)
  - Giảm coupling với test scripts

---

## 6.3 Analysis & Reporting Module

### **Bug Detection / Analyzer (LLM)**
- Phân tích lỗi từ execution

### **Reporting System**
- Hiển thị / export kết quả

---

# 🔁 7. Data Flow (end-to-end)

1. Input URL  
2. LLM → sinh test cases  
3. Playwright → chạy test  
4. Sinh logs / screenshot  
5. LLM → phân tích bug  
6. Report Generator → xuất report  

---

