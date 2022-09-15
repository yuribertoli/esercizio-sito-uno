<template>
  <header>

    <div id="left-header">
        <img src="../assets/img/logo.png" alt="logo">
    </div>

    <div id="central-header">
        <nav>
            <ul>
                <li> <a href="#">About Us</a> </li>
                <li> <a href="#">Info</a> </li>
                <li> <a href="#">Products</a> </li>
                <li> <a href="#">Contact Us</a> </li>
            </ul>
        </nav>
    </div>

    <div id="right-header">
        <!-- cambio classe all'hover per visualizzare un'icona differente di font awesome -->
        <i  @mouseover="isHovering = true" 
            @mouseout="isHovering = false"
            :class="isHovering ? 'fa fa-user' : 'fa fa-sign-in'" 
        ></i>
    </div>

  </header>
</template>

<script>
export default {
    name: 'MyHeader',

    data() {
    return {

      isHovering: false,

    }
  },

}
</script>

<style lang="scss" scoped>
header {
    height: 70px;
    width: 100%;
    position: sticky;
    background-color: black;
    top: 0;
    left: 0;
    z-index: 999;
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: white;

    #left-header {
        height: 100%;
        display: flex;
        align-items: center;
        margin-left: 5%;

        img {
            height: 70%;
            width: auto;
            
            &:hover {
                cursor: pointer;
            }
        }
    }

    #central-header {
        ul {
            display: flex;
            
            a {
                color: white;
                text-decoration: none;
                margin: 0 25px;

                &:hover {
                    text-decoration: underline;
                }
            }
        }
    }

    #right-header {
        margin-right: 5%;
        min-width: 20px;

        i {
            font-size: 1.5rem;
            color: rgb(66, 175, 194);

            &:hover {
                cursor: pointer;
            }
        }
    }
}
</style>