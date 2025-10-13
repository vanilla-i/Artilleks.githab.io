# Artilleks.githab.io
Одностраничный HTML + СSS сайт для соревнования Артиллекс. 

Основной градиент фона
background: linear-gradient(135deg, #1e3c72 0%, #2a5298 50%, #6dd5ed 100%);

.small-heading - заголовки раундов

.special-paragraph - параграфы с pre-line переносами

.text-size - уменьшенный текст (0.7em)

.red-stringi - текст с отступом (красная строка)(text-indent: 60px)

.vertical-space - вертикальные отступы (margin-top/bottom: 1em)

.rule-card - карточки правил с glass-effect

.timeline-item - элементы временной шкалы

.special-paragraph2 белый цвет, нежирное начертание компирование текста 1 в 1.

Немного о скрипте

1. Нахождение формы на странице по ID и "слушаем" событие отправки
document.getElementById('registrationForm').addEventListener('submit', function(e) {
    
2. Отмена стандартного поведение формы (перезагрузку страницы)
    e.preventDefault();(опционально)
    
3. Собираем все данные из формы в удобный объект
    const data = new FormData(this);
    
4. Формируем текст сообщения для Telegram
    const message = `Новая заявка:
Команда: ${data.get('teamName')}
Капитан: ${data.get('captainName')}
Email: ${data.get('email')}
Участников: ${data.get('teamSize')}
Состав: ${data.get('experience')}`;

5. Отправляем запрос к API Telegram
    fetch(`https://api.telegram.org/bot7881799800:AAHKMlXp97ulYsPU4x7iVNkdSGRTY1usFfc/sendMessage`, {
        method: 'POST', // Метод HTTP-запроса
        headers: {'Content-Type': 'application/json'}, - Указание типа данных
        body: JSON.stringify({ - Преобразование данных в JSON-строку
            chat_id: '1002753283159', - ID чата куда отправлять
            text: message - Текст сообщения
        })
    })
6. Если отправка успешна - показываем уведомление
    .then(() => alert('Заявка отправлена!'))
7. Если ошибка - показываем сообщение об ошибке
    .catch(() => alert('Ошибка!'));});
