<script>
export default {
  name: 'InserirMorador',
  template: require('./form.html'),
  data () {
    return {
      sub_title: 'Cadastro de Morador',
      morador: {
        tipoPessoa: { id: 2 }
      }
    }
  },
  methods: {
    save () {
      this.$store.dispatch('newMorador', this.morador)
        .then(() => {
          this.$store.dispatch('getUpdateConfirmModal', {show: true, message: 'Morador inserido com sucesso!!!'})
          this.$router.push('/admin/morador')
          this.$store.dispatch('getMoradores')
        })
    },
		validateBeforeSubmit() {
      this.$validator.validateAll().then((result) => {
        if (result) {
          // eslint-disable-next-line
          return this.save();
        }
      });
    }
  },
}
</script>

<style lang="scss">
  .btn-salvar {
    margin: 0 1em;
  }
</style>
