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
 
        <!-- compare all'hover dell'icona sopra, resta attivo finché c'è hover -->
        <div v-show="isHovering"
            @mouseover="isHovering = true" 
            @mouseout="isHovering = false"
            id="sign-in-up">
            
            <div id="talkbubble"> <!-- box sign-in o sign-up all'hover sull'icona -->

                <div id="talkbubbletriangle" 
                :class="colorTriangle ? 'sameTriangleTrue' : 'sameTriangleFalse'"></div>

                <ul>
                    <li @mouseover="colorTriangle = true"
                        @mouseout="colorTriangle = false" 
                        id="sign-in">
                        <a href="#">
                            <i class="fa fa-hand-spock-o"></i>Sign-In
                        </a>
                    </li>
                    <li id="sign-up">
                        <a href="#">
                            <i class="fa fa-hand-peace-o"></i>Sign-Up
                        </a>
                    </li>
                </ul>

            </div>

        </div>

    </div>

  </header>
</template>

<script>
export default {
    name: 'MyHeader',

    data() {
    return {

      isHovering: false,
      colorTriangle: false,
    }
  },

}
</script>

<style lang="scss" scoped>
@import "../assets/style/variables.scss";

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
        position: relative;

        i {
            font-size: 1.5rem;
            color: $colorMouseOut;

            &:hover {
                cursor: pointer;
            }
        }

        #sign-in-up {
            position: absolute;
            top: 0;
            right: 20px;
            z-index: 1000;
            width: 100px;

            #talkbubble { //box di messaggio sign-in e sign-up
                width: 120px;
                height: 80px;
                background: $colorMouseOut;
                position: relative;
                top: 10px;
                right: 50px;
                -moz-border-radius: 10px 0px 10px 10px;
                -webkit-border-radius: 10px 0px 10px 10px;
                border-radius: 10px 0px 10px 10px;

                ul {
                    display: flex;
                    flex-direction: column;
                    align-items: center;
                    justify-content: center;
                    height: 100%;
                    width: 100%;

                    #sign-in a{
                        border-radius: 10px 0 0 0; 
                    }

                    #sign-up a{
                        border-radius: 0 0 10px 10px; 
                    }

                    li {
                        width: 100%;
                        height: 50%;
                        
                        a {
                            display: block;
                            height: 100%;
                            width: 100%;
                            text-align: center;
                            line-height: 40px;
                            color: white;
                            text-decoration: none;

                            &:hover {
                                text-decoration: underline;
                                background-color: $colorMouseOver;
                            }
                        }

                        i {
                            color: white;
                            font-size: 0.9rem;
                            margin-right: 5px;
                        }
                    }
                }
            }

            //per colorare il triangolo in alto a destra dello stesso colore dell'hover
            .sameTriangleFalse { 
                border-top: 20px solid $colorMouseOut;
            }

            .sameTriangleTrue {
                border-top: 20px solid $colorMouseOver;
            }

            #talkbubbletriangle { //triangolo in alto a destra
                content: "";
                position: absolute;
                left: 100%;
                top: 0px;
                width: 0;
                height: 0;
                border-right: 20px solid transparent;

                #triangle-color {
                    border-top: 20px solid $colorMouseOver;
                }
            }
        }
    }
}
</style>