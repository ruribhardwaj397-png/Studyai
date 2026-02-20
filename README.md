# Studyai
Free AI homework solver and study assistant for students. Generate answers, notes, and summaries using AI.
<!DOCTYPE html>
<html>
<head>
<title>StudyAI Pro</title>

<style>

body{
font-family: Arial;
background: linear-gradient(to right,#4facfe,#00f2fe);
text-align:center;
padding:20px;
color:white;
}

textarea{
width:90%;
height:120px;
padding:10px;
border-radius:10px;
border:none;
}

button{
padding:10px;
margin:5px;
border:none;
border-radius:5px;
background:#222;
color:white;
cursor:pointer;
}

button:hover{
background:#555;
}

#output{
background:white;
color:black;
padding:20px;
margin-top:20px;
border-radius:10px;
}

</style>

</head>

<body>

<h1>🎓 StudyAI Professional Tool</h1>

<textarea id="input" placeholder="Enter your topic or notes"></textarea>

<br>

<button onclick="runPrompt('Summarize this: ')">Summarize</button>

<button onclick="runPrompt('Generate questions from: ')">Questions</button>

<button onclick="runPrompt('Explain simply: ')">Explain</button>

<button onclick="runPrompt('Create flashcards from: ')">Flashcards</button>

<button onclick="runPrompt('Create study plan for: ')">Study Plan</button>

<button onclick="runPrompt('Answer this question: ')">Solve Doubt</button>

<button onclick="runPrompt('Create quiz from: ')">Quiz</button>

<button onclick="runPrompt('Make short notes: ')">Short Notes</button>

<button onclick="runPrompt('Define this: ')">Definition</button>

<button onclick="runPrompt('Give examples of: ')">Examples</button>


<div id="output">

Result appears here

</div>


<script>

async function runPrompt(prompt){

let input=document.getElementById("input").value;

let response=await fetch(

"https://api-inference.huggingface.co/models/google/flan-t5-base",

{

method:"POST",

headers:{

"Content-Type":"application/json"

},

body:JSON.stringify({

inputs: prompt + input

})

});

let result=await response.json();

document.getElementById("output").innerText=result[0].generated_text;

}

</script>


</body>
</html>
