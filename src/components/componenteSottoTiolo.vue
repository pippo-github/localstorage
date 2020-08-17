<template>
    

        <div id='mainBlockSottoTitoloComponent'>

                

                <p id='paragrafoSottoTitolo'>
                        {{ componente_sottotitolo_titolo }}
                </p>

        </div>


</template>




<script>

    export default
    {
        data()
        {
            return{
                componente_sottotitolo_titolo: "This app show you how save data from your browser localy, with localstorage js object."
            }
        }
    }

</script>





<style scoped>

#mainBlockSottoTitoloComponent
{
    background: rgb(43, 6, 104);
    border-radius: 5px;

}

#paragrafoSottoTitolo
{
    color: rgb(230, 199, 199);
    font-size: 1.3em;
    padding: 7px;
}

</style>
