# TODO – Sprawdzenie relacji między encjami Model bazy danych

Repozytorium zawiera:
- **plik 1** – definicje tabel (DDL)
- **plik 2** – dane testowe (INSERT)

---

## 1. Relacje główne, klucze obce

### 🔹 Role → Student
- [x] `Student.role_id` → `Role.role_id`
- [x] Relacja **1:N** (jedna rola – wielu studentów)
- [ ] Czy ograniczyć role tylko do słownika (ENUM / CHECK)?

---

### 🔹 Student → Enrollment → Course
- [x] `Enrollment.student_id` → `Student.student_id`
- [x] `Enrollment.course_id` → `Course.course_id`
- [x] Relacja **N:M** Student–Course
- [x] Unikalność zapisu (`UNIQUE(student_id, course_id)`)
- [ ] Czy dodać `ON DELETE CASCADE`?

---

### 🔹 Student → Grade ← Course
- [x] `Grade.student_id` → `Student.student_id`
- [x] `Grade.course_id` → `Course.course_id`
- [ ] Czy dodać walidację wartości oceny (np. 2.0–5.0)?
- [ ] Czy rozróżnić wiele ocen tego samego typu?

---

### 🔹 Student → Schedule
- [x] `Schedule.student_id` → `Student.student_id`
- [x] Relacja **1:1** (UNIQUE na `student_id`)
- [ ] Czy jeden student może mieć plan na wiele semestrów?

---

### 🔹 Schedule → ClassSession
- [x] `ClassSession.schedule_id` → `Schedule.schedule_id`
- [x] Relacja **1:N** (wiele zajęć w planie)
- [x] `ClassSession.course_id` → `Course.course_id`
- [ ] Czy zajęcia mogą kolidować czasowo?

---

### 🔹 Student → Notification
- [x] `Notification.student_id` → `Student.student_id`
- [ ] Czy dodać statusy jako słownik?
- [ ] Czy przechowywać historię zmian statusu?

---

### 🔹 Student → Payment
- [x] `Payment.student_id` → `Student.student_id`
- [ ] Czy jeden student może mieć wiele płatności (raty)?
- [ ] Czy dodać walidację `status`?

---

### 🔹 Student → Loan
- [x] `Loan.student_id` → `Student.student_id`
- [ ] Czy dodać status zwrotu książki?
- [ ] Czy jeden student może wypożyczyć wiele książek?

---

## 2. Spójność danych testowych

- [x] Kolejność INSERT zgodna z zależnościami FK
- [x] Brak naruszeń kluczy obcych
- [x] Dane realistyczne (daty, statusy)
- [ ] Czy dodać więcej rekordów testowych?

---

## 3. Status

- [ ] Model zweryfikowany
- [ ] Gotowy do implementacji produkcyjnej
- [ ] Gotowy do prezentacji / obrony

---

