# Програма: Сортування назв розділів документа

# 1. Запитуємо у користувача кількість розділів
while True:
    try:
        n = int(input("Введіть кількість розділів (1–20): "))
        if n <= 0:
            print("❌ Кількість розділів не може бути від’ємною або нульовою.")
            continue
        if n > 20:
            print("❌ Максимум дозволено 20 розділів.")
            continue
        break
    except ValueError:
        print("❌ Введіть ціле число без дробів.")

# 2. Вибір методу сортування
print("\nОберіть метод сортування:")
print("1 — за алфавітом (A–Я)")
print("2 — у зворотному порядку (Я–A)")
print("3 — за довжиною назви")

while True:
    method = input("Ваш вибір (1/2/3): ")
    if method in ["1", "2", "3"]:
        break
    else:
        print("❌ Введіть лише 1, 2 або 3.")

# 3. Введення назв розділів
sections = []
for i in range(n):
    title = input(f"Введіть назву розділу №{i+1}: ")
    sections.append(title.strip())

# 4. Видалення дублікатів
sections = list(set(sections))

# 5. Сортування за обраним методом
if method == "1":
    sections.sort()
elif method == "2":
    sections.sort(reverse=True)
else:
    sections.sort(key=len)

# 6. Вивід результату
print("\n✅ Відсортовані розділи:")
for i, title in enumerate(sections, 1):
    print(f"{i}. {title}")
