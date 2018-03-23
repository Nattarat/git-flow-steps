# Git Flow Steps

## Introduction
* ขั้นตอนการนำ Project ที่อยู่บน Source control ต่างๆ (Server) เช่น GitHub, GitLab, Bitbucket ลงมาในเครื่องของเรา (Local) เพื่อทำการพัฒนา
* ขั้นตอนที่นำเสนอจะอ้างอิงตัวอย่างโดยใช้ GitHub และใช้ Command line ในการจัดการ

## Clone step
1. ดาวน์โหลด Project จาก GitHub(Server) ลงมาที่ Local (เช่น D:\localhost)
    ```
    git clone https://github.com/Nattarat/gitstudy.git
    ```

    ![Git Step 1](https://raw.githubusercontent.com/Nattarat/git-flow-steps/master/README-images/git-step-1.jpg)

2. cd เข้า Project folder ที่ดาวน์โหลดลงมา
    * เช็คว่าตอนนี้อยู่ Branch ไหน เพื่อป้องกันการทำงานผิด Branch
    * โดย Default จะเป็น Branch 'master' ถ้าเจ้าของ Repository ไม่ได้ Set default branch ไว้เป็นอย่างอื่น

    ```
    cd gitstudy
    ```

    ![Git Step 2](https://raw.githubusercontent.com/Nattarat/git-flow-steps/master/README-images/git-step-2.jpg)

3. ตรวจสอบ Branch ของ Local ว่ามีอะไรอยู่บ้าง
    ```
    git branch
    ```

    ![Git Step 3](https://raw.githubusercontent.com/Nattarat/git-flow-steps/master/README-images/git-step-3.jpg)

4. ทำให้ Local รู้ว่า Branch บน GitHub(Server) ว่ามีอะไรอยู่บ้าง
    ```
    git fetch --all
    ```

    ![Git Step 4](https://raw.githubusercontent.com/Nattarat/git-flow-steps/master/README-images/git-step-4.jpg)

5. ตรวจสอบ Branch ของ Local ว่าสามารถเห็น Branch บน GitHub(Server) แล้ว
    * สีเขียว คือ Branch ที่มีอยู่ใน Local และเรากำลังทำงานอยู่
    * สีแดง คือ Branch ที่ไม่มีอยู่ใน Local แต่มีอยู่บน GitHub(Server)

    ```
    git branch --all
    ```

    ![Git Step 5](https://raw.githubusercontent.com/Nattarat/git-flow-steps/master/README-images/git-step-5.jpg)

6. ดาวน์โหลด Branch ที่อยู่บน GitHub(Server) พร้อมทั้งเปลี่ยนไปทำงานที่ Branch ที่ดาวน์โหลดลงมา
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
