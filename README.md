![Screenshot 2024-11-10 001042](https://github.com/user-attachments/assets/414b97ab-a5c6-4a28-8cd0-aec3e5fc4b85)# Example นี้มีชื่อว่า https_server
โดยการทำงานของ Example นี้คือการทำให้ esp32 เป็น server โดย ตอบสนองต่อคำขอ GET ด้วย Hello Secure World!
#
ขั้นตอนแรกเลือก Example
# ![Screenshot 2024-11-10 001042](https://github.com/user-attachments/assets/41214d26-2531-4001-9c1c-c578089ec0a9)

แล้วกดmenuconfig
# 
เลือก Example Connection Configuration เพื่อแก้ไขชื่อและรหัส wifi และ save
# ![Screenshot 2024-11-10 001248](https://github.com/user-attachments/assets/d172da29-029c-4afc-87e6-28d57a980982)

รันและbuildโปรแกรม
# ![Screenshot 2024-11-10 002059](https://github.com/user-attachments/assets/2f7d2351-a2ab-4419-8f21-c45d390fa50f)

ให้สังเกตุ ip แล้วนำไปเข้าในเบราว์เซอร์ เช่น https://192.168.1.109
![Screenshot 2024-11-10 002357](https://github.com/user-attachments/assets/e8f10c41-2bcb-4ccc-9a5b-af4de2654533)


# แก้ไขเพิ่มเติม
จะสังเกตุได้ว่าในหน้าเบราว์เซอร์ใน code กำหนดให้ Hello Secure World! แต่หน้าเบราว์เซอร์แสดง Header fields are too long
แก้โดยกด menuconfig และค้นหา http
# ![Screenshot 2024-11-10 002620](https://github.com/user-attachments/assets/482085f2-e34a-4a1b-aa43-f50c98d73fe3)

ปรับที่ Max HTTP Request Header Length และ Max HTTP URI Length ให้เป็น 1024 แล้วกด save
# ![Screenshot 2024-11-10 002649](https://github.com/user-attachments/assets/34591686-9d6f-480d-836a-b34a7dae1b7e)

รันและbuildโปรแกรม
# 
เข้าในเบราว์เซอร์ https://192.168.1.34
# ![Screenshot 2024-11-10 003114](https://github.com/user-attachments/assets/18eb7c3b-52fd-4961-ac0e-5add48a0a7fb)

# ![Screenshot 2024-11-10 003130](https://github.com/user-attachments/assets/30df57c8-73b4-413a-bd14-39cf367e8d94)

สามารถแก้ไขข้อความที่หน้าเว็บได้ที่main.c
```
static esp_err_t root_get_handler(httpd_req_t *req)
{
    httpd_resp_set_type(req, "text/html");
    httpd_resp_send(req, "<h1>Hello Visawa!</h1>", HTTPD_RESP_USE_STRLEN);

    return ESP_OK;
}
```
# ![Screenshot 2024-11-10 003420](https://github.com/user-attachments/assets/927a6406-415b-4de1-a104-4ed5bd17a209)

