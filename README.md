# form

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>

    <style>
      .namevalidation,
      .emailvalidation {
        font-size: 8px;
        color: red;
        display: none;
      }
    </style>
  </head>


  <body>


    <form action="" id="f" name="f">
      <div>
        <label for="name">Name</label>
        <input type="text" id="name" name="name" onblur=" FormValidation.namevalidation()" />
        <div class="namevalidation">Please provide a valid name</div>
      </div>

      <div>
        <label for="email">Email</label>
        <input type="text" id="email" name="email" />
        <div class="emailvalidation">Please provide a valid Email</div>
      </div>

      <div>
        <label for="city">City</label>
        <select name="city" id="city">
          <option value="Dhaka">Dhaka</option>
          <option value="Khulna">Khulna</option>
          <option value="Rajshahi">Rajshahi</option>
          <option value="Barishal">Barishal</option>
        </select>
      </div>


      <div class="checkbox">
        <label for="">Gender</label>
        <label for="Male">
          Male
          <input type="radio" id="Male" name="gender" value="Male" />
        </label>
        <label for="Female">
          Female
          <input type="radio" id="Female" name="gender" value="Female" />
        </label>
      </div>


      <div class="checkbox">
        <label for="Bangla">
          Bangla
          <input type="checkbox" id="Bangla" name="subject" value="Bangla" />
        </label>
        <label for="English">
          English
          <input type="checkbox" id="English" name="subject" value="English" />
        </label>
        <label for="Math">
          Math
          <input type="checkbox" id="Math" name="subject" value="Math" />
        </label>
        <label for="ICT">
          ICT
          <input type="checkbox" id="ICT" name="subject" value="ICT" />
        </label>
      </div>


      <div>
        <label for="comment">Comment</label>
        <textarea id="comment" name="comment"></textarea>
      </div>


      <div>
        <input type="submit" />
      </div>

    </form>



<script>

class FormValidation {

  
  static formSubmit() {
    let form = document.getElementById("f");
    form.addEventListener("submit", function (e) {
      e.preventDefault();

      let name = document.getElementById("name").value;
      let email = document.getElementById("email").value;
      let city = document.getElementById("city").value;
      let comment = document.getElementById("comment").value;

      let selectedGender = "";
      let selectedSubject = "";

      let gender = document.getElementsByName("gender");
      let subject = document.getElementsByName("subject");

      Array.from(gender).forEach((g) => {
        if (g.checked) {
          selectedGender += g.value;
        }
      });

      Array.from(subject).forEach((s) => {
        if (s.checked) {
          selectedSubject += s.value + " ";
        }
      });

      let w = open("", "_blank", "width=500,height=400");
      w.document.write(`<h4>Name:${name}</h4>`);
      w.document.write(`<p>Email:${email}</p>`);
      w.document.write(`<p>City:${city}</p>`);
      w.document.write(`<p>Gender:${selectedGender}</p>`);
      w.document.write(`<p>Subject:${selectedSubject}</p>`);
      w.document.write(`<p>Commment:${comment}</p>`);
      w.document.write(`<button onclick="self.close()">close</button>`);
      w.document.write(`<button onclick="print()">Print</button>`);
    });
  }


  static namevalidation() {
        let name = document.getElementById("name").value;
        let pattern = /^[a-zA-Z]{4,6}$/;
        let nametest = pattern.test(name);
        if (nametest) {
          document.getElementById("name").style.border = "1px solid green";
           document.getElementsByClassName("namevalidation")[0].style.display =
            "none";
        } else {
          document.getElementsByClassName("namevalidation")[0].style.display =
            "block";
         document.getElementById("name").style.border = "1px solid red";
        }
 }


  static emailValidation(){
    
      let mail = document.getElementById("email");
        mail.addEventListener("blur", function () {
        let emailPattern = /^[a-zA-Z0-9_]{3,}[@][a-z]{3,}[.][a-z]{2,}$/;

        if(emailPattern.test(this.value)){
           document.getElementById("email").style.border = "1px solid green";
           document.getElementsByClassName("emailvalidation")[0].style.display =
            "none";
        }else{
           document.getElementsByClassName("emailvalidation")[0].style.display =
            "block";
             document.getElementById("email").style.border = "1px solid red";
        }
      });
  }
}

</script>

<!-- <script>

        FormValidation.formSubmit();
        FormValidation.emailValidation();

        let phone="8801761747406"

        let phonePattern=/^\+?8801[3-9][0-9]{8,8}$/;
        console.log(phonePattern.test(phone));
        

    </script> -->
  </body>
</html>
