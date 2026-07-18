# Домашняя работа по теме "Хранение в k8s" --- "Хамуро ИА"

### Задание 1 Том: обмен данными между контейнерами в поде
<img width="1229" height="787" alt="Снимок экрана 2026-07-18 133641" src="https://github.com/user-attachments/assets/6b1be7a4-6f5e-46d8-8fa8-ee072a2969cf" />
<img width="1744" height="990" alt="Снимок экрана 2026-07-18 133649" src="https://github.com/user-attachments/assets/21364613-3571-402e-8c1e-f9f7c19334cb" />
<img width="1750" height="265" alt="Снимок экрана 2026-07-18 133654" src="https://github.com/user-attachments/assets/f5a0a478-2b83-40fe-b886-8495c5f61b78" />
<img width="1240" height="86" alt="Снимок экрана 2026-07-18 133944" src="https://github.com/user-attachments/assets/3c1050b8-74c3-4bb0-a869-eddaa50bcb90" />

### Задание 2. PV, PVC
<img width="676" height="107" alt="Снимок экрана 2026-07-18 134839" src="https://github.com/user-attachments/assets/85e6f0fc-c9d1-45d1-a249-0da16d8b8769" />
<img width="1453" height="74" alt="Снимок экрана 2026-07-18 135250" src="https://github.com/user-attachments/assets/730f37ed-dfb6-4f99-ac8f-e595e1344d63" />
<img width="787" height="408" alt="Снимок экрана 2026-07-18 135543" src="https://github.com/user-attachments/assets/fe16ec39-2be2-483c-a21b-4278b01f4df7" />
<img width="801" height="292" alt="Снимок экрана 2026-07-18 135556" src="https://github.com/user-attachments/assets/fc1cd940-75b9-4847-99a4-c522fedd0a95" />
<img width="903" height="567" alt="Снимок экрана 2026-07-18 135809" src="https://github.com/user-attachments/assets/5957f7f6-a1e2-4e58-81fb-5b33831d3e30" />

PV не удаляется вместе с PVC. Он переходит из статуса Bound в статус Released.   
Почему так происходит: это прямое следствие политики persistentVolumeReclaimPolicy: Retain. Retain означает, что при освобождении тома (удалении привязанного PVC) Kubernetes не трогает ни сам объект PV, ни данные на диске — ответственность за очистку и повторное использование тома полностью передаётся администратору. Это осознанная защита от случайной потери данных: если бы политика была Delete, PV и данные удалились бы автоматически вместе с PVC.   
<img width="820" height="117" alt="Снимок экрана 2026-07-18 135848" src="https://github.com/user-attachments/assets/024a69a5-767a-4961-bd17-714cdd1d8739" />
Файл shared.txt остаётся на диске узла и полностью читаем даже после удаления объекта PV.
hostPath — это не управляемая Kubernetes система хранения. Объект PersistentVolume в API Kubernetes — это лишь описание/ссылка на реальное хранилище, а не само хранилище. Удаление PV удаляет только эту запись из etcd (метаданные Kubernetes), но никак не воздействует на физические данные на диске узла — Kubernetes для hostPath вообще не умеет и не пытается удалять содержимое каталога. Даже при политике Delete для hostPath-томов реальное удаление данных на диске не гарантируется.

### Задание 3. StorageClass

<img width="637" height="131" alt="Снимок экрана 2026-07-18 141159" src="https://github.com/user-attachments/assets/b492a88f-9cfa-4d51-bc88-4a50f95d3060" />
<img width="1898" height="273" alt="Снимок экрана 2026-07-18 141422" src="https://github.com/user-attachments/assets/56b112c9-06ae-4cf9-b5d1-ced74f9c02b0" />
<img width="894" height="409" alt="Снимок экрана 2026-07-18 141427" src="https://github.com/user-attachments/assets/e64a1726-aba5-4b74-a0bd-87fffbcfee3c" />
<img width="1500" height="427" alt="Снимок экрана 2026-07-18 141433" src="https://github.com/user-attachments/assets/0cb883d2-9b41-40e0-bb48-7976f5a4054f" />

В данном задание я привязал используемое pv в подах к конкретной ноде кластера, а именно мой хост, где развернута нода microK8S.

