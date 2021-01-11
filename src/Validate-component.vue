<template>
    <div>
        <slot/>
    </div>
</template>
<script>
  export default {
    name: 'validate-component',
    methods: {
      validate() {
        console.log('Test validate-component uid: ', this._uid)
        for (const childValidateComponent of this.childValidateComponents) {
          childValidateComponent.validate()
        }
      },
      findParentValidateComponent(parent) {
        if(!parent || !parent.$options) {
          return
        }
        if(parent.$options.name === this.$options.name) {
          return parent
        }
        if(parent.$parent) {
          return this.findParentValidateComponent(parent.$parent)
        }
      },
      setValidateComponentToParent(parent) {
        const parentChildComponents = parent.childValidateComponents
        if(parentChildComponents && !parentChildComponents.includes(this)) {
          parentChildComponents.push(this)
        }
      }
    },
    created() {
      this.childValidateComponents = []
      const parentValidateComponent = this.findParentValidateComponent(this.$parent)
      if(parentValidateComponent) {
        this.setValidateComponentToParent(parentValidateComponent)
      }
    }
  }
</script>


