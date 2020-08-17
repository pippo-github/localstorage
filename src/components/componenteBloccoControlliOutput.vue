<template>
    

    <div id='mainBoxControlliOutput' >

            <h1>
                {{ contolliOutputTitolo }}
            </h1>


            
            <div id='outputBox' >




                                <div class='bloccoConenuti' v-for='(elemento, idx) in vettoreObj' v-bind:key=idx>

<!-- OOOOOOOOOOOOOOOOO; {{ vettoreObj[idx].isChecked }} -->

                                    <div class='etichettaContenuto'>
                                        Select memo
                                    </div>

                                    <div class='contenuto'>

                                        <span id='checkSimbolID' class='selezionaElementoCheckIcon' 

                                            v-on:click='vettoreObj[idx].isChecked = !vettoreObj[idx].isChecked; 
                                            SelezionaElemento(idx);' 

                                            v-bind:class='{activeRemove: vettoreObj[idx].isChecked}'
                                        > 


                                                    &check; 

                                                    
                                        </span>

                                    </div>


                                    <div class='etichettaContenuto'
                                        v-bind:class='{elementoSelezionato: vettoreObj[idx].isChecked}'
                                    >
                                    
                                        Date:

                                    </div>



                                    <div class='contenuto' 
                                        v-bind:class='{elementoSelezionato: vettoreObj[idx].isChecked}'
                                    >
                                        {{ elemento.data }}

                                    </div>


                                    <div class='etichettaContenuto'

                                        v-bind:class='{elementoSelezionato: vettoreObj[idx].isChecked}'
                                    >

                                        Title:

                                    </div>


                                    <div class='contenuto' >
                                        
                                        <span
                                            v-bind:class='{elementoSelezionato: vettoreObj[idx].isChecked}'
                                        > 
                                            
                                            {{ elemento.title }}

                                        </span>

                                    </div>


                                    <div class='etichettaContenuto'
                                        v-bind:class='{elementoSelezionato: vettoreObj[idx].isChecked}'
                                    >

                                        ToDo:

                                    </div>


                                    <div class='contenuto'>

                                        <span 
                                            v-bind:class='{elementoSelezionato: vettoreObj[idx].isChecked}'
                                        >
                                        {{ elemento.toDo }}

                                        </span>

                                    </div>


                                    <div class='etichettaContenuto'>

                                        Delete memo!

                                    </div>

                                    <div class='contenuto' title='remove element'>
                                            <svg v-on:click='rimuoviMsg(idx)' id="imgIcoID" version="1.1" xmlns="http://www.w3.org/2000/svg" class='trashIcoSVG' width="30" height="30" fill='white' viewBox="0 0 463 463" xmlns:xlink="http://www.w3.org/1999/xlink" enable-background="new 0 0 463 463"
                                            
                                            v-bind:class='{abilitaRimozioneMsg: vettoreObj[idx].isChecked}'
                                            
                                            >

                                            <path  id="imgIcoIDChrColor" d="M375.5,48H295V31.5C295,14.131,280.869,0,263.5,0h-64C182.131,0,168,14.131,168,31.5V48H87.5C65.72,48,48,65.72,48,87.5v24  c0,4.142,3.357,7.5,7.5,7.5H64v288.5c0,10.336,6.71,19.128,16,22.266v9.734c0,12.958,10.542,23.5,23.5,23.5h256  c12.958,0,23.5-10.542,23.5-23.5v-9.734c9.29-3.138,16-11.93,16-22.266V119h8.5c4.143,0,7.5-3.358,7.5-7.5v-24  C415,65.72,397.28,48,375.5,48z M183,31.5c0-9.098,7.402-16.5,16.5-16.5h64c9.098,0,16.5,7.402,16.5,16.5V48h-97V31.5z M79,159.5  c0-4.687,3.813-8.5,8.5-8.5s8.5,3.813,8.5,8.5V416h-8.5c-4.687,0-8.5-3.813-8.5-8.5V159.5z M359.5,448h-256  c-4.687,0-8.5-3.813-8.5-8.5V431h273v8.5C368,444.187,364.187,448,359.5,448z M168,416h-17V159.5c0-4.687,3.813-8.5,8.5-8.5  s8.5,3.813,8.5,8.5V416z M240,416h-17V159.5c0-4.687,3.813-8.5,8.5-8.5s8.5,3.813,8.5,8.5V416z M312,416h-17V159.5  c0-4.687,3.813-8.5,8.5-8.5s8.5,3.813,8.5,8.5V416z M384,407.5c0,4.687-3.813,8.5-8.5,8.5H367V159.5c0-4.687,3.813-8.5,8.5-8.5  s8.5,3.813,8.5,8.5V407.5z M384,137.597c-2.638-1.027-5.503-1.597-8.5-1.597c-12.958,0-23.5,10.542-23.5,23.5V416h-25V159.5  c0-12.958-10.542-23.5-23.5-23.5S280,146.542,280,159.5V416h-25V159.5c0-12.958-10.542-23.5-23.5-23.5S208,146.542,208,159.5V416  h-25V159.5c0-12.958-10.542-23.5-23.5-23.5S136,146.542,136,159.5V416h-25V159.5c0-12.958-10.542-23.5-23.5-23.5  c-2.997,0-5.862,0.57-8.5,1.597V119h305V137.597z M400,104H63V87.5C63,73.991,73.99,63,87.5,63h288c13.51,0,24.5,10.991,24.5,24.5  V104z"/>

                                            </svg>                                   
                                            
                                         </div>


                                   
                                </div>





            </div>

    </div>


</template>


<script>

import {eventBus} from '../main'

export default{
    data(){
        return{
            contolliOutputTitolo: "OutputBox",
            vettoreObj: []
        }
    },
    methods:
    {
        SelezionaElemento(idxCheckElement)
        {
            // console.log("elemento selezione, cliccato: ", idxCheckElement)
            eventBus.$emit("selezioneCheck", (idxCheckElement))
        },

        rimuoviMsg(idx)
        {
            // console.log("rimozione messaggio: " + idx)
        
                        this.vettoreObj.splice(idx, 1)
                        localStorage.objLocalStarageToDoApp = JSON.stringify(this.vettoreObj)
                    
                        // console.log("oggetto con rimozione effettuata: " , this.vettoreObj)

                        // document.getElementById("imgIcoIDChrColor").classList.remove('activeSelectableRemove')    
        }


    },
    created()
    {

        
        eventBus.$on("datiInviati", (payLoadDeiDati) =>{
            // console.log("outputBox, dati ricevuti: " + payLoadDeiDati)

                this.vettoreObj = ''
                this.vettoreObj = JSON.parse(payLoadDeiDati)

        })

        this.vettoreObj = JSON.parse(localStorage.objLocalStarageToDoApp)

    }
}

</script>


<style scoped>

#mainBoxControlliOutput
{
    border: solid green 1px;
    /* background: rgb(131, 199, 131); */
    background-image: radial-gradient(circle at 77% 26%, rgba(175, 175, 175,0.06) 0%, rgba(175, 175, 175,0.06) 4%,transparent 4%, transparent 100%),radial-gradient(circle at 37% 90%, rgba(129, 129, 129,0.06) 0%, rgba(129, 129, 129,0.06) 55%,transparent 55%, transparent 100%),radial-gradient(circle at 7% 92%, rgba(53, 53, 53,0.06) 0%, rgba(53, 53, 53,0.06) 39%,transparent 39%, transparent 100%),radial-gradient(circle at 65% 17%, rgba(128, 128, 128,0.06) 0%, rgba(128, 128, 128,0.06) 60%,transparent 60%, transparent 100%),radial-gradient(circle at 100% 39%, rgba(75, 75, 75,0.06) 0%, rgba(75, 75, 75,0.06) 20%,transparent 20%, transparent 100%),radial-gradient(circle at 92% 34%, rgba(205, 205, 205,0.06) 0%, rgba(205, 205, 205,0.06) 35%,transparent 35%, transparent 100%),radial-gradient(circle at 63% 90%, rgba(98, 98, 98,0.06) 0%, rgba(98, 98, 98,0.06) 62%,transparent 62%, transparent 100%),radial-gradient(circle at 93% 74%, rgba(130, 130, 130,0.06) 0%, rgba(130, 130, 130,0.06) 65%,transparent 65%, transparent 100%),linear-gradient(90deg, rgb(18, 233, 78),rgb(160, 239, 92));
}


#mainBoxControlliOutput h1
{
    background: rgb(55, 87, 18);
    color: rgb(245, 111, 2);
    text-align: center;
    padding: 7px;
    font-family: 'Courier New', Courier, monospace;

    margin-bottom: 77px;
    margin-top: 3px;
}

#outputBox{
    border: solid pink 2px;
    margin: 11px 0 11px 0;
}

.activeRemove
{
    color: red;
}

/* .activeSelectableRemove
{
    fill: yellow;
} */


#imgIcoIDChrColor:hover
{
    fill: red;
}

/* .unActiveRemove
{
    fill: white;
} */

.selezionaElementoCheckIcon:hover{
    cursor: pointer;
    color: red;
}

.elementoSelezionato
{
    text-decoration: line-through;
}

.etichettaContenuto
{
 background: rgb(11, 56, 11);
 color: white;
 font-size: 1.6em;
 padding: 4px;
 }

.etichettaContenuto:nth-child(1)
{
    text-align: center;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-style: italic;
    
}

.contenuto
{
 background: rgb(19, 7, 59);
 color: white;
 margin-bottom: 33px;
 padding: 8px;
}

.etichettaContenuto:nth-child(3)
{
 color: rgb(182, 171, 171);
}

.etichettaContenuto:nth-child(5)
{
 color: rgb(182, 171, 171);
}

.etichettaContenuto:nth-child(7)
{
 color: rgb(182, 171, 171);
}

.contenuto:nth-child(2)
{
    text-align: center;
}

.contenuto:nth-child(8)
{
    color: rgb(235, 212, 212);
    word-wrap: break-word;
    max-height: 150px;
    overflow-x: hidden;
}

.contenuto{
    color: rgb(235, 212, 212);
    font-family: "Lucida Console";
}

/* testo etichetta: delete msg */
.etichettaContenuto:nth-child(9)
{
    text-align: center;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-style: italic;
}

.contenuto:nth-child(10)
{
    text-align: center;
    margin-bottom: 111px;
    
}


.trashIcoSVG
{
    pointer-events: none;
    position: relative;
    top: 3px;
}

.abilitaRimozioneMsg
{
    pointer-events: auto;
}

.trashIcoSVG:hover
{
 fill: red;
 cursor: pointer;
}



@media (max-width: 576px)
{
    .contenitoreLi{
        /* background: red; */
        position: relative;
        display: block;
        width: 90%;
    }
}


</style>