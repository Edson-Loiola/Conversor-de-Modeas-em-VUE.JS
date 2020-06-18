


<template>
  <div id="app">
           
         <Conversor moeda-a="USD" moeda-b="BRL" />
         <Conversor moeda-a="BRL" moeda-b="USD"/>
         <Conversor moeda-a="EUR" moeda-b="BRL"/>          
       
  </div> 
  
 

</template>




<script>
  import Conversor from "./components/Conversor.vue";
  
  export default {
      name: "app",
      components: {
        Conversor
      },

         }

</script>




<style >

#app .Conversor:first-child{

    margin-top: 10px;
  }


#app {   
  
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: 1fr 1fr 1fr;
  min-height: 90vh;
  align-items: center;
  justify-items: center;
  grid-gap: 8px;
  justify-content: center;  
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #439e3b;

}


/*Media Query*/
@media screen and (min-width: 768px) {
    
    #app{
    
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 1fr;
    width: 768px;
    margin:0 auto;
    align-items: center;
    justify-items: center;
        
    }

    #app .Conversor:first-child{
    margin: 0;
  }

}/* fim Media Query*/




/*Media Query*/
@media screen and (min-width: 1024px) {
    
    #app{    
  
    width: 1024px

    }
}/* fim Media Query*/




html, body{
  margin: 0;
  padding: 0;
  min-height: 100vh;
  background: radial-gradient(rgb(255, 255, 255), #cccccc);
  background-attachment: fixed;
}

footer{
  display: grid;
  align-items: center; 
  background: white;
  min-width: 100vw;
  min-height: 10vh;
  justify-content: center;  
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #707070;
  font-size: 14px;
}

/*Media Query*/
@media screen and (max-width: 768px) {
    
    footer{    
  
       font-size: 11px;
       

    }
}/* fim Media Query*/


</style>
