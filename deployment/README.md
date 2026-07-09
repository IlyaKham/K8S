# Домашнее задание по занятости «Запуск приложений в K8S» --- "Хамуро ИА"

### Задание 1. Создать развертывание и обеспечить доступ к репликам приложения из другого Pod.
1. Создать приложение развертывания, состоящее из двух контейнеров — nginx и multitool. Решить возникшую ошибку.
   <img width="712" height="68" alt="Снимок экрана 2026-07-09 165906" src="https://github.com/user-attachments/assets/bf5257fb-d79e-4e65-9dd1-372f717152bc" />
   <img width="1910" height="516" alt="Снимок экрана 2026-07-09 165858" src="https://github.com/user-attachments/assets/1dbb8f19-106f-46d9-b575-5a37c8c640a7" />
   <img width="780" height="86" alt="Снимок экрана 2026-07-09 170032" src="https://github.com/user-attachments/assets/9ac68e6b-3078-4334-9ab9-fc5f27e038dc" /> 
2. После запуска увеличьте количество реплик рабочего приложения до 2.
   <img width="702" height="88" alt="Снимок экрана 2026-07-09 170151" src="https://github.com/user-attachments/assets/822c80ec-9ef5-44b2-863c-be6ea5c92b4e" />
3. Об уменьшении количества подов до и после масштабирования.  
4. Создать Сервис, обеспечивающий доступ к репликам приложений из п.1.
   <img width="805" height="75" alt="Снимок экрана 2026-07-09 170349" src="https://github.com/user-attachments/assets/0ec63a2c-f98f-4ae0-84da-4a8d8d19f57d" />
   
5. Создайте отдельный модуль с помощью приложения Multitool и убедитесь curl, что из модуля есть доступ к приложениям из п.1.
   <img width="992" height="481" alt="Снимок экрана 2026-07-09 170741" src="https://github.com/user-attachments/assets/5481f232-88f2-47db-b565-2102ebb46382" />

### Задание 2. Создать развертывание и обеспечить запуск основного контейнера при выполнении условий.
1. Создайте приложение развертывания nginx и обеспечьте запуск контейнера только после того, как будет запущен сервис этого приложения.
   <img width="697" height="128" alt="Снимок экрана 2026-07-09 171855" src="https://github.com/user-attachments/assets/35976a45-b2b0-4913-a3ef-5a6f6e1664a9" />
   <img width="680" height="264" alt="Снимок экрана 2026-07-09 172014" src="https://github.com/user-attachments/assets/78e4fdff-bbf5-41c8-95c3-7975f06a2c62" />
   <img width="792" height="384" alt="Снимок экрана 2026-07-09 172034" src="https://github.com/user-attachments/assets/ac89c5ac-f08a-47b9-98bd-e7ffd3bd1a95" />
3. Убедиться, что nginx не запускается. В качестве Init-контейнера возьмите busybox.
4. Создать и запустить Сервис. Убедиться, что Init запустился.
   <img width="853" height="125" alt="Снимок экрана 2026-07-09 172439" src="https://github.com/user-attachments/assets/3966ce93-bda4-4184-bb05-9fadd56f0e6b" />
   <img width="718" height="126" alt="Снимок экрана 2026-07-09 173405" src="https://github.com/user-attachments/assets/c39ac8cb-bac4-4521-a62b-335e5aa884e1" />
   <img width="997" height="205" alt="Снимок экрана 2026-07-09 173513" src="https://github.com/user-attachments/assets/3fca8f62-486d-43c1-b6f2-0d20e56edb99" />

