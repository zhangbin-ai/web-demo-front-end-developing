<script>
export default {
  name: 'MenuItem',
  functional: true,
  props: {
    icon: {
      type: String,
      default: ''
    },
    title: {
      type: String,
      default: ''
    }
  },
  watch: {
    icon(newValue, oldValue) {
      icon = newValue
    }
  },
  render(h, context) {
    const { icon, title } = context.props
    const vnodes = []
    // console.log(icon)
    if(icon && title){
      vnodes.push(
        <div class="sidebar-item">
          <svg-icon icon-class={icon}/>
          <span slot='title'>{(title)}</span>
        </div>
      )
    }

    // <my-icon iconClass={icon}  size="20px"/>
    // if (icon) {
    //   // if (icon.includes('el-icon')) {
    //   //   vnodes.push(<i class={[icon, 'sub-el-icon']} />)
    //   // } else {
    //   //   // vnodes.push(<svg-icon icon-class={icon}/>)
    //   //   vnodes.push(<my-icon iconClass="shouye" color="#00ff00" size="20px"/>)
    //   // }
    //   vnodes.push(<my-icon iconClass="shouye" color="#00ff00" size="23px"/>)
    // }
    // if (title) {
    //   vnodes.push(<span slot='title'>{(title)}</span>)
    // }
    return vnodes
  }
}
</script>

<style lang="scss" scoped>
// .sub-el-icon {
//   color: currentColor;
//   width: 2em;
//   height: 2em;
// }
.sidebar-item{
  line-height: 60px;
  .svg-icon{
    // color:aqua;
    // margin-top:20px;
    // margin-right:3px;
    // padding-left:3px;
  }
  span{
    margin-left:-5px;
    float: right;
  }
}
</style>
