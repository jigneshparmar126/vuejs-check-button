# vuejs-check-button
Vue js check button for vue developer easy to use 

# How it works 
it is simple and you can modify it as per your need.
it accepts only true or false as model you can used it in loop like selecting and deselecting products
you can change parent components values or objects value on change of value of this components

# Props that can be passed to this Component

<table>
     <tr> 
        <th>Props </th>
        <th>Default </th>
         <th>Type </th>
        <th>Description </th>
     </tr>   
     <tr>
          <td>name</td>
          <td>NULL </td>
          <td>String </td>
          <td>It allows you pass your any variable value or static string like "'is_agree'" </td>
     </tr>    
      <tr>
          <td>checked</td>
          <td>false </td>
          <td>Boolean </td>
          <td>It allows you pass your any variable value as Boolan like "true or false" </td>
     </tr>  
      <tr>
          <td>v-model</td>
          <td>false </td>
          <td>Boolean </td>
          <td>It allows you pass your any variable value as Boolan like "true or false" </td>
      </tr>  
   <tr>
          <td>disabled</td>
          <td>false </td>
          <td>Boolean </td>
          <td>It allows you pass your any variable value as Boolan like "true or false" </td>
      </tr>  
</table>   

# Example
```
 <check-button
                                :name="'is_agree'"
                                :checked="true"
                                v-model="is_agree"
                                @change="onChange"
                        />
```

#full example

```
<script>
   import CheckButton from "../form/Switch";
  export default{
  components: {
      CheckButton
      },
       methods:{
            submitForm($type){
               
            },
            onProductSubsrcibe(value){
                console.log(value);
            },
            onChange(value){
                console.log(value);
            }
        },
  }
 </script> 
<template>
   <div>
     <table>
      <tr v-for="(product,key) in initialData.subscription">
          <td>
              <div class="col-md-10">
                  <p>{{ product.name }} </p>
                   <div class="col-md-2 text-right">
                   <check-button :name="getName(key)" @change="onProductSubsrcibe" :checked="product.value" v-model="product.value" />
              </div>
          </td>
      </tr>
    </table>
    <table>
       <tbody>
                <tr >
                    <td width="90%"><h4>Pauzeer je abonnement</h4></td>
                    <td >
                        <check-button
                                :name="'is_agree'"
                                :checked="true"
                                v-model="is_agree"
                                @change="onChange"
                        />

                    </td>
                </tr>
    </table>
    </div>
</template>                
 ```               

