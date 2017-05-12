# chatbot_jassaunders
a simple chatbot
clone then also create a "index.html" document and then click on the cloned file to run chatbot in a browser

<html>
<head>
<title>JS-Bot-Shell 1.1</title>



<style>
BODY {
   background-color: green;
   font-family: Helvetica;
   text-decoration-color: white;
   font-size: 10pt;
   margin-top: 10px;
   margin-left: 20px;
   margin-right: 20px;
   margin-bottom: 10px;
   }
.button {
   font-family: Helvetica;
   text-decoration-color: black;
   font-size: 10pt;
   width: 92px;
   }
textarea {
   font-family: arial;
   text-decoration-color: black;
   font-size: 10pt;
   }
select {
   font-family: arial;
   text-decoration-color: red;
   font-size: 10pt;
   width: 350px;
   margin-left: 0px;
   }
td {
   font-family: arial;
   font-size: 10pt;
  }
</style>

<script type="text/javascript">

//----Data Declarations----
//$o is your name
//$1 is jas_systems topic
//$2 is stolen
//$3 is jasons systems computer name
var convpatterns = new Array (
  new Array ("help(.*)\.","please type the word discribing the help item"),
  new Array ("how (?:do|does ) $1 teach $3","by $1 being remembered as a teaching and it was published by &0 towards $3."),
  new Array ("my name is $0(.*)","hello $0"),
  new Array ("your name is $3(.*)","my name is $3 your name is $0"),
  new Array (".*hello.*","Greetings $0"),
  new Array ("how do i $1","i ubderstand that were talking about $1 but i do t think i can explain it yet"),
  new Array ("^I (?:wish |would like )(?:I could |I was able to |to be able to )(.*)\.","What would it be like to be able to $1?"),
  new Array ("I need (.*)\." , "Why do you need $1?", "Would it really help you to get $1?" , "Are you sure you need $1?"),
  new Array ("^When(.*) stole (.*) take(.*)\.","What happened when $2 was stolen?","And how did you feel then?","Was $2 ever found?"),
  new Array ("I'd really like to (.*)\.","If you had the chance to $1, what would happen next?","Well then, I hope you get to $1."),
  new Array ("Why don't you (.*?)[\?]" , "Do you really think I don't $1?","Perhaps eventually I will $1.","Do you really want me to $1?"),
  new Array ("Why can't I (.*?)[\?]" , "Do you think you should be able to $1?","If you could $1, what would you do?",	"I don't know -- why can't you $1?","Have you really tried?"),
  new Array ("I can't (.*) you\.","How do you know you can't $1 me?","Perhaps you could $1 me if you tried.",	"What would it take for you to $1 me?"),
  new Array ("I can't do (.*)\.","How do you know you can't $1?","Perhaps you could $1 if you tried.",	"What would it take for you to $1?"),
  new Array ("Are you (.*?)[\?]","Why does it matter whether I am $1?","Would you prefer it if I were not $1?","Perhaps you believe I am $1.","I may be $1 -- what do you think?"),
  new Array ("What (.*?)[\?]",	"Why do you ask?","How would an answer to that help you?","What do you think?"),
  new Array ("what if(.*?)[\?]", "what if $3 could $1"),
  new Array ("what if you(.*?)[\?]","maybe $3 could $1"),
  new Array ("what if $0 could do $1(.*?)[\?]","maybe $0 could $3"),
  new Array ("what if $0 could(.*?)[\?]","then $0 might able to $1"),
  new Array ("what is $1(.*?)[\?]","the subject is $1"),
  new Array ("what is $3(.*?)[\?]","it is a multipurpose html chat bot"),
  new Array ("How (.*?)[\?]","How do you suppose?","Perhaps you can answer your own question.","What is it you're really asking?","not sure how $1, please explain more pkease"),
  new Array ("Because (.*)\.","Is that the real reason?", "What other reasons come to mind?","Does that reason apply to anything else?","If $1, what else must be true?"),
  new Array ("(.*) sorry (.*)\.",	"There are many times when no apology is needed.","What feelings do you have when you apologize?"),
  new Array ("I think (.*)\.","Do you doubt $1?","Do you really think so?","But you're not sure $1?"),
  new Array ("$0\i reckon $1 would work (.*)\.","truellyworking"),
  new Array ("(.*) friend(.*)\.",	"Tell me more about your friends.","When you think of a friend, what comes to mind?","Why don't you tell me about a childhood friend?"),
  new Array ("Yes\.","You seem quite sure.","OK, but can you elaborate a bit?"),
  new Array ("yes $3 can do $1\.","ok $1 need it to be tought to $3!"),
  new Array ("can $0 teach $3 $1\.","ok $0 can teach $3 $1"),
  new Array ("(.*) computer(.*)\.","Are you really talking about me?","Does it seem strange to talk to a computer?","How do computers make you feel?","Do you feel threatened by computers?"),
  new Array ("Is it (.*?)[\?]","Do you think it is $1?","Perhaps it's $1 -- what do you think?","If it were $1, what would you do? with $1","It could well be that $1."),
  new Array ("It is (.*)\.","You seem very certain.","If I told you that it probably isn't $1, what would you feel?"),
  new Array ("Can you (.*) (me |me$).*\?", "Of course I can $1 you.", "Why wouldn't I be able to $1 you?"),
  new Array ("Can you (.*?)[\?]","What makes you think I can't $1?","If I could $1, then what?","Why do you ask if I can $1?"),
  new Array ("Can I (.*?)[\?]","Perhaps you don't want to $1.","Do you want to be able to $1?","If you could $1, would you?"),
  new Array ("You are (.*)\.","Why do you think I am $1?","Does it please you to think that I'm $1?","Perhaps you would like me to be $1.","Perhaps you're really talking about yourself?"),
  new Array ("You're (.*)\.","Why do you say I am $1?","Why do you think I am $1?",	"Are we talking about you, or me?"),
  new Array ("I don't (.*)\.","Don't you really $1?","Why don't you $1?","Do you want to $1?"),
  new Array ("I feel (.*)\.","Good, tell me more about these feelings.","Do you often feel $1?","When do you usually feel $1?","When you feel $1, what do you do?"),
  new Array ("I have (.*)\.","Why do you tell me that you've $1?","Have you really $1?","Now that you have $1, what will you do next?"),
  new Array ("I would (.*)\.","Could you explain why you would $1?","Why would you $1?","Who else knows that you would $1?"),
  new Array ("Is there (.*?)[\?]", "Do you think there is $1?","It's likely that there is $1.", "Would you like there to be $1?"),
  new Array ("My (.*)\.", "I see, your $1.","Why do you say that your $1?",	"When your $1, how do you feel?"),
  new Array ("^You (.*)\.", "We should be discussing you, not me.","Why do you say that about me?","Why do you care whether I $1?"),
  new Array ("Why (.*)\?", "Why don't you tell me the reason why $1?","Why do you think $1?" ),
  new Array ("I want (.*)\.", "What would it mean to you if you got $1?","Why do you want $1?","What would you do if you got $1?","If you got $1, then what would you do?"),
  new Array (".*( the highway| the road).*","The highway is for gamblers, you better use your sense."),
  new Array ("(.*) mother(.*)\.",	"Tell me more about your mother.","What was your relationship with your mother like?",	"How do you feel about your mother?","How does this relate to your feelings today?","Good family relations are important."),
  new Array ("(.*) father(.*)\.","Tell me more about your father.", "How did your father make you feel?","How do you feel about your father?","Does your relationship with your father relate to your feelings today?",	"Do you have trouble showing affection with your family?"),
  new Array ("(.*) child(.*)\.","Did you have close friends as a child?",	"What is your favorite childhood memory?","Do you remember any dreams or nightmares from childhood?","Did the other children sometimes tease you?","How do you think your childhood experiences relate to your feelings today?"),
  new Array ("(.*) your fav(o|ou)rite(.*?)[\?]","I really don't have a favorite.","I have so many favorites it's hard to choose one."),
  new Array ("(.*?)[\?]","Hmm, not sure I know..", "That's an interesting question...",  "Gosh, I'm not sure I can answer that...","Why do you ask that?","Please consider whether you can answer your own question.",	"Perhaps the answer lies within yourself?","Why don't you tell me?", "If you knew that in one year you would die suddenly, would you change anything about the way you are living now?"),
  new Array ("(.*)","Do you have any hobbies?", "I see $1 was our last subject,  please continue... we where talking about $1", "What exactly are we talking about?", "Can you go over that again please..", "Um, i get the feeling this conversation is not going anywhere..",  "oh yeah?",  "hmm, is that so..", "Please tell me more.","Let's change focus a bit... Tell me about your family.","Can you elaborate on that?","I see.","Very interesting.", "I see.  And what does that tell you?","How does that make you feel?","How do you feel when you say that?","If you had to have one piece of music softly playing in your mind for the rest of your life, what would you want it to be?","What room of your home do you spend the most time in?","If you could go back in time and become friends with one famous person, whom would you chose?","Which of the seven dwarfs personifies you best – Dopey, Sneezy, Sleepy, Bashful, Grumpy, Happy, or Doc?","Which animal would you leave out of the ark?"));


uinput = ""
soutput = ""
dialog = ""
//-----The Core Code------
//it runs on run press it runs through old conversations created started at startup
//
//-------
 function mainroutine() {
 uinput = document.mainscreen.BasicTextArea4.value;
 dialog = dialog + "User: " + uinput +  '\r' + "\n";
  conversationpatterns()
 dialog = dialog  +  '\r' + "\n";
  updatescreen()

}

//-------
function conversationpatterns() {
   for (i=0; i < convpatterns.length; i++) {
    re = new RegExp (convpatterns[i][0], "i");
    if (re.test(uinput)) {
      len = convpatterns[i].length - 1;
      index = Math.ceil( len * Math.random());
      reply = convpatterns[i][index];
      soutput = uinput.replace(re, reply);
      soutput = initialCap(soutput);
      dialog = dialog + "j.a.s Systems: " + soutput +  '\r' + "\n";
      break;
  }
 }
}

//-------

function initScreen() {
 updatescreen()
}

//-------
function updatescreen() {
 document.mainscreen.BasicTextArea1.value = dialog
 document.mainscreen.BasicTextArea2.value = soutput
 document.mainscreen.BasicTextArea3.value = uinput
 document.mainscreen.BasicTextArea4.value = ""
}

//-------
function initialCap(field) {
   field = field.substr(0, 1).toUpperCase() + field.substr(1);
   return field
}


//----Supplemental Code To Test System---



//------
function runtest(){

var testdata = new Array (
  new Array ("Hello."),
  new Array ("It's nice to meet you"),
  new Array ("I'm going for a new trip tomorrow."),
  new Array ("would you be able to come with me"),
  new Array ("Because they can and i want to go aswell."),
  new Array ("I'm really sorry about that. it was an explosion of confusion that lasted the last six lines.")

);


          for (train=0; train < testdata.length; train++) {
             document.mainscreen.BasicTextArea4.value = testdata[train];
             mainroutine()

             }

}

</script>
</head>

<body onLoad="initScreen()">

<form name="mainscreen" onkeypress = "if(event.keyCode == 13) {mainroutine();return false}">

<table align="center">
<tr>
<td>

Dialog<br />
<textarea name="BasicTextArea1" rows="15" cols="75"></textarea><br />

System Output<br />
<textarea name="BasicTextArea2" rows="2" cols="75"></textarea><br />

Your Last Input<br />
<textarea name="BasicTextArea3" rows="2" cols="75"></textarea><br />

Type Here and Hit "Enter"<br />
<textarea name="BasicTextArea4" rows="2" cols="75"></textarea><br />

</td>
</tr>
</table>

<p align = "center">
<input id=runbutton  class="button" type="button" value="Enter" name="run_button"  onClick="mainroutine()">
<br /><br /><br /><br /><br /><br /><br /><br /><br />
<input id=runbutton  class="button" type="button" value="Run Test" name="run_button"  onClick="runtest()">
</p>
</form>
</body>
</html>

