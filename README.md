# laravel_received_queue_redis

Tutorial Instalasi
1. Create new project in local computer
2. Install redis package in project: composer require predis/predis
3. Clone this project
4. Copy file in app/Console/Commands/SendQueueEmail.php
5. Copy file in app/Console/Kernel.php
6. Copy file in app/Mail/TestingMail.php
7. Copy file in resources/views/welcome.blade.php

the program will automatically run every 5 minutes, if redis have data to be sent via email.
