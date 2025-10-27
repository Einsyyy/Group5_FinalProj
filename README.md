# Group5_FinalProj

**UE - CALOOCAN: Engineering Borrowing System**
- The purpose of this proposal is to provide a system for borrowing materials from different departments in a more organized and efficient way. It allows the process of borrowing materials faster and easier to manage for both the students and administrators.

---

## 📋Project Proposal Link
[View project proposal](https://docs.google.com/document/d/1C1Fj5pqExZpKPn4mpm2bcv4sN5IOBOHy_f1UPy8jEzI/edit?usp=sharing)

## Figma Prototype Link
[View Figma Prototype](https://www.figma.com/design/n0EnTU04S89XkaVkO9EXfT/Untitled?node-id=2-55&t=KCDde4V3du0Zy3dX-1)

---


## 👤Group 5 Members
- **Park, Chang Hyun**
- **Joven, Rakim**
- **Bacus, Romulo**
- **Gargaritano, Edieson**
- **Tampus, Jevric**
- **Velasquez, Jeremy**

## Task Distribution

### JOVEN:
- **Login/Signup/UML**
    - **UML**
        - Adjust accordingly sa UI/UX ng figma natin
        - Revise yung mga classes na hindi na need such as yung database
        - As for the access modifiers wala nmn comment si sir kanina so okay nmn na siguro.
          
    - **Login / Signup**
        - Need na niya ng form validation
        - Option to sign up as a student, faculty, or admin.
        - Sa signup, maglagay ng First Name, Last Name, as well as Student number.
---

### VELASQUEZ:
- **About Us/Help Page**
    - **About Us**
        - Description kung about san yung project natin
        - Picture ng mga members (Formal mas better parang 2x2 lang)
        - Names ng members na rin

    - **Help Page**
        - Patulong kay Joven about dito, mainly mga FAQs on how ginagamit yung system natin
        - Atleast mga 6-8 questions and answers to those siguro would suffice.
---

### GARGARITANO:
- **Dashboard**
    - **Status Update**
        - Pwede maview yung latest transactions (Request, For approval, Claimed)
        - Need na visible yung mga info such as kung ano ung mga hiniram, sino yung prof, ano oras hiniram, pati kung kelan tapos nung time.
          
    - **Notification**
        - Hawak siya ni admin and faculty kung ano update sa mga pending na borrow forms
        - Announce if merong notice na ipapaalam sa students such as if magkakaron ng maintenance, or may mga bagong gamit na available na sa toolroom.
---

### BACUS:
- **Cart**
    - **Cart**
        - Makikita lahat dito ng inadd to cart na items from the departments
        - Suggested here ni sir is pwedeng humiram ng gamit from multiple departments, lalagyan nlng label from where siya
        - Meron siyang option to **edit** and **confirm**
          
    - **Edit Cart**
        - Dito nmn is hahayaan yung user (student) na mag edit if may gusto siya tanggalin sa list ganon, or iadd, makikita nmn sa figma yung sample
        - Then Ayun pwede mong iclose (X) or click **confirm** if okay na yung edit mo
          
    - **Cart Overview**
        - Pag nag confirm na si user sa mga items na need niya, ireredirect na siya sa page na to, bale sa cart overview, ito yung parang pinaka verification if sure ka nasa mga hihiramin mong gamit
        - May option parin diyan to **edit** or **confirm** if sure na
        - Makikita na din diyan yung **professor in charge** so make sure na meron diyan, dropdown button siya so ippresent yung list of faculty for that.

    - **Official Borrow Form**
        - So after mo iconfirm yung cart mo, lalabas na etong borrow form, kita na diyan yung name, student no, prof in charge, as well as yung reference number
        - Sa **reference number**, iggenerate siya after mag confirm sa cart overview, bale need nlng ng random generator to make it unique every transaction.
---

### TAMPUS:
- **History**
    - **Search Bar Feature**
        - May database tayo for the transactions so ang gusto ni sir mangyari dito is allowed na magsearch and magsort depende sa gusto ni user
        - Allowed magsearch according to **date, department, sinong prof, etc**
        - Makikita lahat ng transactions na nacomplete here
    

