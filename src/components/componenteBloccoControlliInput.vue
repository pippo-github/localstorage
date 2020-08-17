<template>


    <div id='bloccoControlliMainBox'>


        <div id='labelBloccoControlli'>
             {{ title_blocco_controlli }}
        </div>


        <div id='bloccoControlli'>

                <form  v-on:submit.prevent="onSubmit">

                    <div class='controlloAndLabel'>
                        <label class='controlli' > Title </label> <input  class='controlli' type="text" v-model="titleValue"
                        v-on:focusout='controllaInput()'
                        >
                    </div>

                    <div class='controlloAndLabel'>
                        <label class='controlli' > To do </label> <input  class='controlli' type="text" v-model="toDoValue" 
                         v-on:focusout='controllaInput()'
                        >
                    </div>

                    <div class='controlloAndLabel'>
                        <label class='controlli' > data/time </label> <input  class='controlli' type="datetime-local" v-model="dateValue"
                         v-on:focusout='controllaInput()'
                        >
                    </div>


                    <div id='msgAllValueNeeded'>
                                {{ all_value_needed_msg }}
                    </div>

                    <div class='controlloAndLabel'>
                        <input id='btnSubmit' class='controlli' type="submit" value='send memo'>
                    </div>




                </form>

        </div>



    </div>


</template>


<script>

/*eslint-disable*/

import {eventBus} from '../main'

export default {
    data()
    {
        return{

            title_blocco_controlli: "Input controls",
            all_value_needed_msg: "all values are necessaries, please fill all fileds",
            titleValue: '',
            toDoValue: '',
            dateValue: '',
            allValueAreOK: false,
            toDoObj:
            [

            ],
            numOfObj: 0,
   
   

        }
    },

    created()
    {
        let convertiToObj = JSON.parse(localStorage.objLocalStarageToDoApp)
        this.toDoObj = convertiToObj
        

//  console.log("CURRRRRRR localstorage: ", convertiToObj)

        this.toDoObj = []
        this.toDoObj = convertiToObj


        eventBus.$on("selezioneCheck", (datiIdxCheckElement) =>{
            console.log("selezioneCheck: " + datiIdxCheckElement)
        })
    },

    methods:
    {
        onSubmit(){
            // console.log("on submit")
            if(this.titleValue == '' || this.toDoValue == '' || this.dateValue == '')
            {
                console.log("tutti i valori devono essere presenti");
                document.getElementById('msgAllValueNeeded').style.display = 'block'                
            }
            else
            {
                // document.getElementById('msgAllValueNeeded').style.display = 'none'
                this.allValueAreOK = true;

                this.numOfObj = Object.keys(this.toDoObj).length;


                    if(localStorage.objLocalStarageToDoApp)
                    this.toDoObj = JSON.parse(localStorage.objLocalStarageToDoApp)

                                    this.toDoObj.push(
                                    {
                                            id: this.numOfObj,
                                            title: this.titleValue,
                                            toDo: this.toDoValue,
                                            data: this.dateValue,
                                            isChecked: false
                                    })               


                                    this.numOfObj ++;


                document.getElementById('msgAllValueNeeded').style.display = 'none'

                let ObjTostringa = JSON.stringify(this.toDoObj)

                localStorage.objLocalStarageToDoApp = '';
                localStorage.objLocalStarageToDoApp = ObjTostringa


                eventBus.$emit("datiInviati", (ObjTostringa))

 
 this.titleValue = this.toDoValue = this.dateValue = ''
 

            }
        },




        controllaInput()
        {
            if(this.allValueAreOK)
            document.getElementById('msgAllValueNeeded').style.display = 'none'

            // console.log("controlla input")
        }
    }
}
</script>


<style scoped>

#labelBloccoControlli
{
    width: 100%;
    background: rgb(8, 8, 61);
    text-align: center;
    color: white;
    font-size: 1.7em;
    font-family: "Lucida Handwriting";

}

.controlloAndLabel
{
    display: flex;
    margin-top: 11px;
}



.controlli:nth-child(1){
    color: rgb(192, 205, 221);
    font-family: Arial, Helvetica, sans-serif;
    font-family: "Lucida Handwriting";
    font-size: 22px;
    padding: 7px;
    font-weight: 200;
    font-style: italic;
}


#msgAllValueNeeded
{
    border: solid red 1px;
    margin: 11px 0 11px 0;
    padding: 7px;
    font-size: 1.4em;
    background: rgb(170, 60, 60);
    color: white;
    display: none;
}

.showMsg
{
    display: block;
}

#btnSubmit
{
    background: rgb(53, 53, 97);
    color: white;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-weight: 900;
    transition: 1s;

    border: none;
    border-radius: 5px;
    margin-bottom: 5px;
}

#btnSubmit:hover{
background: rgb(8, 8, 44);
cursor: pointer;
color: lightgreen;
}
    


.controlli{
    flex: 1;
}

</style>