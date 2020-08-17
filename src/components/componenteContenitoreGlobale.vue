<template>
    

        <div id='contenitoreGlobaleMainBox'>


                <!-- <div>
                    {{ componente_globale }}
                </div> -->

                <componente-titolo />
                <!-- <componente-sotto-titolo /> -->
                <componente-controlli-input />
                <componente-controlli-output />

        </div>




</template>


<script>

import componenteTitolo from './componenteTitolo'
// import componenteSottoTitolo from './componenteSottoTiolo';
import componenteBloccoControlliInput from './componenteBloccoControlliInput';
import componenteBloccoControlliOutput from './componenteBloccoControlliOutput';


export default {
    
    components:
    {
        'componente-titolo': componenteTitolo,
        // 'componente-sotto-titolo': componenteSottoTitolo,
        'componente-controlli-input': componenteBloccoControlliInput,
        'componente-controlli-output': componenteBloccoControlliOutput,
    },

    data()
    {
        return{
            componente_globale: "componente globale eseguito"
        }
    },
    created()
    {
        // console.log("contenitore globale creato")
        // alert(localStorage.objLocalStarageToDoApp)
    }
}
</script>