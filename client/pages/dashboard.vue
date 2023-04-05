<template>
<div>
  <b-row>
    <b-col cols="6" class="mx-auto">
      <b-card>
        <b-card-title class="text-capitalize">Welcome {{$auth.user.name}} </b-card-title>
      </b-card>
    </b-col>
  </b-row>
</div>
</template>

<script>
export default {
  middleware: 'auth'
}
</script>
