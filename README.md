# Service-Oriented-Architecture-lab2

## Connect to helios
```bash
ssh -p 2222 -L 26505:localhost:26505 -o ServerAliveInterval=15 s265058@se.ifmo.ru
```

## JAX-RS service

**Второй веб-сервис** должен располагаться на URL `/demography`, и реализовывать ряд дополнительных операций, связанных с вызовом API первого сервиса:

- `/eye-color/{eye-color}/percentage`: вывести долю людей с заданным цветом глаз в общей популяции (в процентах)
- `/nationality/{nationality}/eye-color/{eye-color}/percentage`: вывести долю людей с заданным цветом глаз в пределах указанной национальности (в процентах)
Эти операции также должны размещаться на отдельных URL.

Второй веб-сервис должен быть реализован на фреймворке JAX-RS, развёрнут в окружении под управлением сервера приложений WildFly и вызывать REST API первого сервиса.

Доступ к обоим сервисам должен быть реализован с по протоколу https с самоподписанным сертификатом сервера. Доступ к сервисам посредством http без шифрования должен быть запрещён.

Оба веб-сервиса и клиентское приложение должны быть развёрнуты на сервере helios.

keytool -exportcert -keystore helios.p12 -alias helios -keypass helios -storepass helios -file helios.crt