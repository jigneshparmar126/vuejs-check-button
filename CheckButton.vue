<template>
    <label class="button-check">
        <input :class="classes" type="checkbox" :checked="checked" :name="name" :disabled="disabled" v-model="value" @change.stop="change(value)">
        <span class="btn-round" :class="{'active': value}">
            <slot>
                   <span class="off" :class="{'hide': value}"></span>
                   <span class="on" :class="{'hide': !value}"></span>
            </slot>
        </span>
        <span class="label-text" v-if="label">{{ label }}</span>
    </label>
</template>
<script>
    export default {
        props: {
            disabled: Boolean,
            classes: String,
            checked: Boolean,
            name: String,
            label:String
        },
        data() {
            return {
                value: null
            }
        },
        beforeMount() {
            this.value = this.checked
        },
        mounted() {
            this.$emit('input', this.value)
        },
        watch: {
            value(val) {
                this.$emit('input', val)
            },
            checked (val) {
                this.value = val
            },
            disabled(){
               if(this.disabled){
                   this.value = false;
               }
            }
        },
        methods:{
            change(obj,value){
                this.$emit('change',obj,value) ;
            }
        }
    }
</script>
<style>
    input[type="checkbox"] {
        display: none;
    }
    label.button-check{
        width:auto;
        margin-right:30px;
        position:relative ;
    }
    label.button-check .btn-round{
        width: 22px;
        height: 22px;
        background-color:#FFF;
        border-radius: 50%;
        display:inline-block;
        border:1px solid #EAEAEC;
        position:absolute;
        top:2px;
    }
    .label-text{
        display:inline-block;
        margin-left:40px;
        font-weight:normal;
        top:-10px;
    }
    label.button-check .active span.on{
        content: '';
        position: absolute;
        width: 7px;
        height: 11px;
        -webkit-transform: rotate(45deg);
        transform: rotate(45deg);
        top: 3px;
        z-index: 1;
        left: 7px;
        -webkit-transition: top ease-in-out .25s;
        transition: top ease-in-out .25s;
        border-bottom: 1px solid #FFF;
        border-right: 1px solid #FFF;
    }
</style>
