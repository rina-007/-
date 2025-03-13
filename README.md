# Интеграция новой вёрстки в WordPress сайт sg-forma.com

## Описание проекта
Данный проект представляет собой интеграцию новой вёрстки в существующий WordPress сайт sg-forma.com. Новая вёрстка включает в себя обновленный дизайн и структуру страниц, сохраняя при этом существующий функционал.

## Структура проекта
```
├── src/
│   ├── assets/         # Изображения, иконки и другие медиафайлы
│   ├── style/          # CSS файлы
│   └── script/         # JavaScript файлы
├── *.html              # HTML шаблоны страниц
└── README.md          # Документация проекта
```

## План интеграции

### 1. Подготовка
- [ ] Создание резервной копии текущего сайта
- [ ] Создание дочерней темы WordPress
- [ ] Перенос ресурсов из папки `src` в соответствующие директории темы

### 2. Создание шаблонов страниц
- [ ] `front-page.php` (на основе index.html)
- [ ] `page-about.php` (about-us.html)
- [ ] `page-contacts.php` (contacts.html)
- [ ] `page-delivery.php` (delivery.html)
- [ ] `archive-products.php` (для страниц категорий товаров)
- [ ] `single-product.php` (для карточек товаров)
- [ ] `page-profile.php` (profile.html)
- [ ] `page-cart.php` (basket.html)
- [ ] `page-favorites.php` (favorites.html)

### 3. Интеграция функционала
- [ ] Настройка меню в `functions.php`
- [ ] Создание Custom Post Types для товаров
- [ ] Интеграция корзины и избранного
- [ ] Настройка форм регистрации и авторизации

### 4. Перенос стилей и скриптов
- [ ] Подключение CSS файлов через `wp_enqueue_styles()`
- [ ] Подключение JS файлов через `wp_enqueue_scripts()`
- [ ] Адаптация путей к изображениям и другим ресурсам

## Требования
- WordPress 5.0 или выше
- PHP 7.4 или выше
- MySQL 5.6 или выше
- Доступ к FTP или файловому менеджеру хостинга
- Права на редактирование файлов темы

## Инструкция по установке

### 1. Создание резервной копии
```bash
# Создание резервной копии базы данных
wp db export backup.sql

# Создание резервной копии файлов
tar -czf wp-content-backup.tar.gz wp-content/
```

### 2. Создание дочерней темы
1. Создать директорию `sg-forma-child` в папке `wp-content/themes/`
2. Создать файл `style.css`:
```css
/*
Theme Name: SG Forma Child
Theme URI: https://sg-forma.com
Description: Дочерняя тема для SG Forma
Author: Your Name
Author URI: https://sg-forma.com
Template: sg-forma
Version: 1.0.0
*/
```

3. Создать файл `functions.php`:
```php
<?php
function sg_forma_child_enqueue_styles() {
    wp_enqueue_style('parent-style', get_template_directory_uri() . '/style.css');
    wp_enqueue_style('child-style',
        get_stylesheet_directory_uri() . '/style.css',
        array('parent-style')
    );
}
add_action('wp_enqueue_scripts', 'sg_forma_child_enqueue_styles');
```

### 3. Перенос ресурсов
1. Скопировать содержимое `src/assets` в `wp-content/themes/sg-forma-child/assets`
2. Скопировать CSS файлы из `src/style` в `wp-content/themes/sg-forma-child/style`
3. Скопировать JS файлы из `src/script` в `wp-content/themes/sg-forma-child/script`

### 4. Создание шаблонов страниц
1. Создать необходимые файлы шаблонов в директории дочерней темы
2. Адаптировать HTML код из соответствующих .html файлов
3. Добавить необходимые WordPress функции и хуки

## Тестирование
После интеграции необходимо проверить:
- [ ] Корректное отображение всех страниц
- [ ] Работу форм и функционала
- [ ] Адаптивность на разных устройствах
- [ ] Скорость загрузки страниц
- [ ] SEO-параметры

## Поддержка
При возникновении проблем:
1. Проверить логи ошибок WordPress
2. Проверить консоль браузера на наличие ошибок
3. Убедиться в корректности путей к файлам
4. Проверить права доступа к файлам

## Безопасность
- Регулярно обновлять WordPress и плагины
- Использовать безопасные методы хранения данных
- Проверять входные данные форм
- Использовать nonce для форм

## Контакты
При возникновении вопросов обращаться к:
- Email: [your-email@example.com]
- Телефон: [your-phone]

## Лицензия
[Указать тип лицензии] 