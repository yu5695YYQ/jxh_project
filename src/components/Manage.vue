<template>
    <div class="menu_admin">
        <a-menu mode="inline" :open-keys="openKeys"
                style="position: relative"
                theme="dark"
                :default-selected-keys="defaultSelectedKeys"
                @openChange="menuOpenChange"
                @click="menuTrigger">
                <a-menu-item key="1">
                    <a-icon type="appstore"/>
                    ant 菜单1
                    <!--<router-link to="/"></router-link>-->
                </a-menu-item>
                <a-menu-item key="2">
                    <a-icon type="user"/>
                    ant 菜单2
                </a-menu-item>
                <a-menu-item key="3"><a-icon type="calendar"/> ant 菜单3</a-menu-item>
                <a-sub-menu key="sub1">
                    <template slot="title"><a-icon type="setting"/>  ant 菜单4</template>
                    <a-menu-item key="test:1">test1</a-menu-item>
                    <a-menu-item key="test:2">test2</a-menu-item>
                    <a-menu-item-group >
                        <span slot="title"><a-icon type="qq"/>item1</span>
                        <a-menu-item key="item:1">option1</a-menu-item>
                    </a-menu-item-group>
                </a-sub-menu>
                <a-sub-menu key="sub5">
                    <span slot="title"><a-icon type="mail"/> ant 菜单5</span>
                    <a-menu-item key="test:5">test5</a-menu-item>
                    <!--<a-sub-menu>
                        <span slot="title">子菜单</span>
                    </a-sub-menu>-->
                </a-sub-menu>

        </a-menu>
        <slot></slot>
  </div>
</template>

<script>
// @ is an alias to /src
import { Icon, Menu } from 'ant-design-vue'
export default {
    name: 'ManageApi',
    components: {
        AIcon:Icon,
        AMenu:Menu,
        ASubMenu:Menu.SubMenu,
        AMenuItem:Menu.Item,
        AMenuItemGroup:Menu.ItemGroup,
    },
    data(){
        return {
            rooteSubmenuKey:['sub1','sub5'],
            openKeys:['sub1'],
            defaultSelectedKeys:['1']
        }
    },
    created(){
//        console.log('create 初始化')
    },
    mounted(){
//        console.log('dom 加载完成')
    },
    methods:{
        menuOpenChange(openKeys){
            const latestOpenKey = openKeys.find(key => this.openKeys.indexOf(key) === -1);
            if (this.rooteSubmenuKey.indexOf(latestOpenKey) === -1) {
                this.openKeys = openKeys;
            } else {
                this.openKeys = latestOpenKey ? [latestOpenKey] : [];
            }
        },
        menuTrigger(item){
            let self = this;
            switch (item.key){
                case '1':
                    self.$router.push('/home');break;
                case '2':
                    self.$router.push('/about');break;
                case '3':
                    self.$router.push('/user');break;
            }
        },
    }
}
</script>
<style lang="scss">
    .menu_admin{
        width: 256px;
        height: 100%;
        .ant-menu-inline{
            height: 100%;
        }
    }
</style>
<style src="../assets/css/normalize.css"></style>