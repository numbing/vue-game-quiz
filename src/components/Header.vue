<template>
 <div>
 <b-nav tabs>
     <b-nav-item disabled>Fancy question</b-nav-item>
     <b-nav-item disabled>Counter:{{numberofCorrect}}/{{numberOfTotal}}</b-nav-item>
 </b-nav>
</div>
</template>
<script>
export default {
    props:[
        'numberofCorrect',
        'numberOfTotal'
    ]
}
</script>