

<template>

   
            <div class="Conversor" >                         

                <h2>{{moedaA}} to {{moedaB}}</h2>
                <input class="field" type="text" v-model="moedaA_value" v-bind:placeholder="moedaA">
                <input class="button" type="button" value="Converter" v-on:click="validar">
            
                <h3>{{moedaB_value}}</h3>    
                
                
            </div>
   

</template>    




<script>


        export default {
            name: "Conversor",
            props:["moedaA","moedaB"],

            mounted(){     

                this.converter();

            },
            data(){
            return{
                
                        moedaA_value: 1,
                        moedaB_value: 0                  
        
                    };
                },

           methods:{   /* função com a api que converte */
                
        
        validar(){


            if(this.moedaA_value == ""){
            
                 this.moedaB_value = "$ 0.00"                 

             }else 
               
                if(isNaN(parseFloat(this.moedaA_value))){

                    this.moedaB_value = "Incorrect value!"
                  
                                    
            }else{
                                
                        this.converter()   
                                            
            }

        },


        
 
            
  
           
              converter(){                       

                     
                    let de_para = this.moedaA + "_" + this.moedaB;                    
                   
                    let url = "https://free.currconv.com/api/v7/convert?q="+ de_para  +"&compact=ultra&apiKey=5515d23ee3a125cb08f2"

                    fetch(url).then(res => { return res.json()
                        })
                   
                          .then(json=>{
                            
                            if(json.error){
                                     //{"status":400,"error":"Free API limit reached."}
                                    this.moedaB_value = "Limited reached!"

                            }else {                         
                            
                                let cotacao = json[de_para]                                                                       
                                  this.moedaB_value = "$ " + (cotacao * parseFloat(this.moedaA_value)).toFixed(2)
                               
                            }

                                   
                                                                                 
                         })

                             
                }              

            }//moetod
        
        };


    
</script>


<style scoped>



 /* Caixa contorno   */
.Conversor{  
   
    min-height: 120px;
    min-width: 210px;
    box-sizing: border-box;
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.5);    
    border-radius: 8px;
    background: white;
    border-left: 15px solid rgb(96, 121, 107);    
    transition-duration: 0.5s;

     }
     


/*Media Query*/
@media screen and (min-width: 1024px) {

            .Conversor{
            min-height: 180px;
            min-width: 300px;
            
        
            }


            #app h2{ 
                font-size: 30px;
                
            }

             #app h3{
                font-size: 25px;
                
            }

            #app .field{
                width: 90px;
            }

} /* fim Media Query*/




.Conversor h2{ 
    font-size: 16px;    
}

.Conversor h3{
    font-size: 16px;
}

.Conversor .field{
    width: 70px;
}

.Conversor .button{
    
    font-size: 16px;    
    background-color: rgb(96, 121, 107);
    color: white;

}





</style>
