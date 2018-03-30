# Git daily work flow

## Introduction
* ขั้นตอนการนำ Project ที่อยู่บน Source control ต่างๆ (Server) เช่น GitHub, GitLab, Bitbucket ลงมาในเครื่องของเรา (Local) เพื่อทำการพัฒนา
* ขั้นตอนที่นำเสนอจะอ้างอิงตัวอย่างโดยใช้ GitHub และใช้ Command line ในการจัดการ

## 1. Download project from server to local
* ดาวน์โหลด Project จาก GitHub(Server) ลงมาที่ My Computer(Local) (เช่น D:\localhost)
    ```
    git clone https://github.com/Nattarat/gitstudy.git
    ```

    ![Git Step 1](https://raw.githubusercontent.com/Nattarat/git-flow-steps/master/README-images/git-step-1.jpg)

* cd เข้า Project folder ที่ดาวน์โหลดลงมา
    ```
    cd gitstudy
    ```
    - เช็คว่าตอนนี้อยู่ Branch ไหน เพื่อป้องกันการทำงานผิด Branch
    - โดย Default จะเป็น Branch 'master' ถ้าเจ้าของ Repository ไม่ได้ Set default branch ไว้เป็นอย่างอื่น

    ![Git Step 2](https://raw.githubusercontent.com/Nattarat/git-flow-steps/master/README-images/git-step-2.jpg)

## 2. Configure the email address and author name to be used with your commits
* ตั้งค่า Email address และ Author name ของเราที่จะใช้ Commit เฉพาะ Repository นี้
    - Email ต้องเป็นของ Account ที่ Source control นั้นๆ และได้รับสิทธิ์ในการ Commit
    - Author name ชื่อที่เราใช้ Commit ตั้งอะไรก็ได้ (ไม่ใช่ Username ที่ผูกกับ Account ที่ Source control)
    ```
    // ตั้งค่า Author name เฉพาะ Repository นี้
    // กรณีต้องการตั้งค่าแบบ Global ให้เว้น space แล้วใส่ --global ต่อท้าย config
    git config user.name "Tode"

    // ตั้งค่า Email address เฉพาะ Repository นี้
    // กรณีต้องการตั้งค่าแบบ Global ให้เว้น space แล้วใส่ --global ต่อท้าย config
    git config user.email "nattarat.design@gmail.com"

    // ตรวจเช็คการตั้งค่าของ Local repository
    git config --local --list
    ```

    ![Git Config Step 1](https://raw.githubusercontent.com/Nattarat/git-flow-steps/master/README-images/git-step-config-1.jpg)

## 3. Check how many branch in local repository
* ตรวจสอบ Local repository ว่ามี Branch อะไรอยู่บ้าง
    ```
    git branch
    ```

    ![Git Step 3](https://raw.githubusercontent.com/Nattarat/git-flow-steps/master/README-images/git-step-3.jpg)

* ทำให้ Local repository รู้ว่าบน GitHub(Server) มี Branch อะไรอยู่บ้าง
    ```
    git fetch --all
    ```

    ![Git Step 4](https://raw.githubusercontent.com/Nattarat/git-flow-steps/master/README-images/git-step-4.jpg)

* ตรวจสอบ Local repository ว่าสามารถเห็น Branch บน GitHub(Server) แล้ว
    - สีเขียว คือ Branch ที่มีอยู่ใน Local และเรากำลังทำงานอยู่
    - สีแดง คือ Branch ที่ไม่มีอยู่ใน Local แต่มีอยู่บน GitHub(Server)

    ```
    git branch --all
    ```

    ![Git Step 5](https://raw.githubusercontent.com/Nattarat/git-flow-steps/master/README-images/git-step-5.jpg)

## 4. Change branch for feature working
* การพัฒนาเว็บไซต์ เราจะไม่พัฒนาที่ Master branch โดยตรง เพราะ Branch นี้เราจะรักษาไว้ให้โค้ดที่ผ่านการ Test ผ่านและเตรียมไว้ใช้ Merge เข้า Production branch เท่านั้น
* ดังนั้นการพัฒนาเว็บไซต์ เราจะทำการแตก Branch แยกออกมาจาก Master branch *** โดยจุดประสงค์และการตั้งชื่อของ Branch จะเป็นไปตาม Flow ที่ตกลงกันภายในทีม
* โดยการพัฒนาเว็บไซต์ที่มีขนาดเล็ก - ใหญ่ จะมีลักษณะ Branch ที่ไม่ซับซ้อน ตัวอย่างเช่น
```
* master
|\  \  \
| |  |  |
| |  |
| * feature_1
| |  |
| |  |
|/   * feature_2
|    |
* master + feature_1
|    |
|   /
|  /
| /
* master + feature_1 + feature_2
|
|
```


* ขั้นตอนการบันทึก Account(Email/Password) เพื่อไม่ต้องใส่ทุกครั้งเมื่อ push
  - credential.helper store คือ เปิดการใช้งานการบันทึก Account(Email/Password) ลงที่ Global หรือ Local git (default เป็น false)
```
$ git config credential.helper store
$ git push http://example.com/repo.git
Username: <type your username>
Password: <type your password>

[several days later]
$ git push http://example.com/repo.git
[your credentials are used automatically]
```



* ดาวน์โหลด Branch ที่อยู่บน GitHub(Server) พร้อมทั้งเปลี่ยนไปทำงานที่ Branch ที่ดาวน์โหลดลงมา
* git checkout -b tode คือ เปลี่ยนไปทำงานที่ Branch นั้นๆ
* --track origin/tode คือ ตั้งค่าการ Add/Delete/Modify, Commit, Push ไปที่ Branch นั้นๆ

    ```
    git checkout -b tode --track origin/tode
    ```

    ![Git Step 6](https://raw.githubusercontent.com/Nattarat/git-flow-steps/master/README-images/git-step-6.jpg)

7. ตรวจสอบ Branch ของ Local ที่มีอยู่และกำลังทำงานอยู่อีกครั้ง
    * สีขาว คือ Branch ที่มีอยู่ใน Local แล้ว
    * สีเขียว คือ Branch ที่มีอยู่ใน Local และเรากำลังทำงานอยู่
    * สีแดง คือ Branch ที่ไม่มีอยู่ใน Local แต่มีอยู่บน GitHub(Server)

    ```
    git branch --all
    ```

    ![Git Step 7](https://raw.githubusercontent.com/Nattarat/git-flow-steps/master/README-images/git-step-7.jpg)

## Add/Delete/Modify, Commit, Push step
