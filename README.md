// Assignment code here
let specialcharacters=['!','@','#','$','%','^','&','*','(',')'];
let lowercase=['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z'];
let upercase=['A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z'];
let numbers=['0','1','2','3','4','5','6','7','8','9'];

// Get references to the #generate element
var generateBtn = document.querySelector("#generate");



function generatePassword(length,containspecial,containslower,containsuper,containsnumbers){
      let groups=[];
      if(containspecial){
        groups.push(specialcharacters);
      
      }
      if(containslower){
        groups.push(lowercase);

      }
      if(containsuper){
        groups.push(upercase);}


      if(containsnumbers){
          groups.push(numbers);}

      let password="";   
      for(let index=0;index < length;index++){
            let group=groups[index%groups.length];
            var item = group [Math.floor(Math.random()*group.length)];
            password+=item;
      }    
      return password;
}

     


// Write password to the #password input
function writePassword() {
  var passwordText = document.querySelector("#password");
  var passwordlength = document.getElementById("passwordlength");
  var length = parseInt(passwordlength.value); 
  passwordText.value = password;
  var specialcheck= document.getElementById("specialcharacter");
  var isspecialcheck = specialcheck.checked;
  // do the same for lowercase, upper, and numbers check box
  var lowercase=document.getElementById("lowercase");
  var islowercase = lowercase.checked;
  var upercaseelement=document.getElementById("upercase");
  var isupercaseelement = upercaseelement.checked;
  var isnumberselement =document.getElementById("numeric");
  var isnumbers = isnumberselement.checked; 

  var password = generatePassword(length, isspecialcheck,islowercase,isupercaseelement, isnumbers);
  

passwordText.value=password;

}

// Add event listener to generate button
generateBtn.addEventListener("click", writePassword);
