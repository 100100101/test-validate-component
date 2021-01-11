<template>
  <!-- 1 -->
  <validate-component ref="test">
    <some-component>
      <!-- 2 -->
      <validate-component/>
    </some-component>
    <some-component>
      <!-- 3 -->
      <validate-component>
        <!-- 4 -->
        <validate-component/>
      </validate-component>
    </some-component>
    <!-- 5 -->
    <validate-component/>
  </validate-component>
</template>

<script>
import ValidateComponent from './components/Validate-component'
import SomeComponent from './components/Some-component'
export default {
  components: {
    ValidateComponent,
    SomeComponent
  },
  mounted() {
    this.$refs.test.validate()
  }
}
</script>


