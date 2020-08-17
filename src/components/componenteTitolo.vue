<template>
    <div>

    

        <div class='componenteTitolo'>

            {{ componente_titolo }}

        </div>

            <div class='componenteTitolo'>

                    <div>
                        {{ componente_sottotitolo_titolo }}
                    </div>

                    <div>
                        {{ componente_sottotitolo_titolo2 }}
                    </div>

            </div>


    </div>

</template>



<script>

 export default
 {
     data()
     {
         return{
             componente_titolo: "Basic todo app, with localstorage",
             componente_sottotitolo_titolo: "This app show you how save data from your browser localy, with localstorage js object, for HTML5.",
             componente_sottotitolo_titolo2: "Insert a memo and refresh the page, after the memo has been sent, the values ​​are stored permanently in your browser until you decide to delete them."

         }
     }
 }

</script>


<style scoped>

.componenteTitolo
{
    width: 100%;
    background: rgb(43, 6, 104);
    color: orange;
    font-size: 1.3em;
    font-family: "Bernard MT", "Berlin Sans FB", verdana;
    /* color: white; */
    padding: 11px;
    box-sizing: border-box;
    border-radius: 5px;
    margin-bottom: 16px;
}

.componenteTitolo:nth-child(2)
{
    margin-bottom: 33px;
    font-family:  "Berlin Sans FB", verdana;

}

.componenteTitolo div{
    color: white;
    font-size: .77em;
    
    margin: 0px 0px 0px 0px;
}

</style>