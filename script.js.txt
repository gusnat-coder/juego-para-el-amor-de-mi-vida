
// ==========================
// CONFIGURACIÓN GENERAL
// ==========================


const music = document.getElementById("music");


const screens = document.querySelectorAll(".screen");





// ==========================
// CAMBIO DE PANTALLAS
// ==========================


function nextScreen(id){


    screens.forEach(screen => {

        screen.classList.remove("active");

    });


    const next = document.getElementById(id);


    if(next){

        next.classList.add("active");

    }



    window.scrollTo({

        top:0,

        behavior:"smooth"

    });


}




// ==========================
// COMENZAR HISTORIA
// ==========================


function startStory(){


    playMusic();


    nextScreen("intro");


}





// ==========================
// MÚSICA
// ==========================


function playMusic(){


    music.volume = 0.5;


    music.play().catch(()=>{


        console.log("La música necesita interacción del usuario");


    });


}




// ==========================
// RESPUESTAS DEL JUEGO
// ==========================


function correctAnswer(){


    const message = document.getElementById("answerMessage");


    message.innerHTML =

    "Exacto ❤️ La persona más especial es Natasha.";



    setTimeout(()=>{


        nextScreen("capitulo2");


    },2000);



}




function wrongAnswer(){


    const message = document.getElementById("answerMessage");


    message.innerHTML =

    "Creo que esa respuesta necesita otra oportunidad 😭❤️";



}





// ==========================
// CORAZONES FLOTANDO
// ==========================


function createHeart(){


    const container = document.getElementById("hearts");


    if(!container) return;



    const heart = document.createElement("div");



    heart.className="heart";


    heart.innerHTML="❤️";



    heart.style.left =

    Math.random()*100 + "%";



    heart.style.fontSize =

    (Math.random()*20+15)+"px";



    heart.style.animationDuration =

    (Math.random()*5+5)+"s";



    container.appendChild(heart);



    setTimeout(()=>{


        heart.remove();



    },8000);



}




setInterval(createHeart,500);


// ==========================
// CARTA ANIMADA
// ==========================


const letter = `

Natasha ❤️


Quería hacer algo diferente para vos.

Algo que no fuera solamente un mensaje,
sino un pequeño lugar donde guardar
una parte de nuestra historia.


Gracias por cada sonrisa,
cada momento y cada recuerdo.

Gracias por ser una persona tan especial
en mi vida.


Espero que cuando veas esto,
puedas sentir todo el cariño
con el que fue creado.


Porque detrás de cada palabra,
cada imagen y cada línea de código,
hay una intención:

recordarte lo importante que sos para mí.


Esta historia recién comienza...


Con muchísimo amor ❤️


Agustín

`;



function openLetter(){


    nextScreen("carta");


    writeLetter();


}




function writeLetter(){


    const text = document.getElementById("letterText");


    if(!text) return;



    text.innerHTML="";



    let index=0;



    const interval = setInterval(()=>{


        text.innerHTML += letter[index];


        index++;



        if(index >= letter.length){


            clearInterval(interval);


        }



    },40);



}







// ==========================
// VOLVER AL COMIENZO
// ==========================


function restartStory(){


    screens.forEach(screen=>{


        screen.classList.remove("active");


    });



    document

    .getElementById("inicio")

    .classList.add("active");



    window.scrollTo({


        top:0,


        behavior:"smooth"


    });



}




// ==========================
// INICIO AUTOMÁTICO SUAVE
// ==========================


document.addEventListener("DOMContentLoaded",()=>{


    createHeart();


});
