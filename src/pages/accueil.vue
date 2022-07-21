<template>
  <div id="main">

      <v-row style="padding: 2% 2% 0% 2%; background-color:#4b548b "> <!--#f5f2f2  #E6E7EB-->
        <v-card-title style=" color: white; font-size: 22px; margin-right:-2%">
           Track My Market - Business
        </v-card-title>
        <v-card-title style="font-weight: bold; color: white; font-size: 23px;">
           / Editeur
        </v-card-title>
      </v-row>

      <v-row id="mapHeader1" align="center" justify="end" style="padding: 1% 2% 2% 2%; background-color:#4b548b; "><!-- height:600px -->
        <v-col cols="12" sm="12" md="12" lg="1" xl="1">
          <v-card-text style="font-size: 18px; color: white;">
            Zoom: 
          </v-card-text>
        </v-col>
        
          
          <v-btn large rounded color="#11101d" @click="zoom(1)">
            <v-icon size="28" style="color: white;" >
                mdi-magnify-plus-outline
            </v-icon> 
          </v-btn>
          <v-btn large rounded color="#11101d" @click="zoom(-1)">
            <v-icon size="28" style="color: white">
                mdi-magnify-minus-outline
            </v-icon>
          </v-btn>
          <v-btn @click="addBlockToMap()">bnbnbn</v-btn>
        
        
      </v-row>
      <v-row id="mapHeader2" justify="center" style="padding: 0% 2% 2% 2%; background-color:#4b548b; height:550px;">
        <v-col  cols="12" sm="12" md="12" lg="11" xl="11">
          
          <!--<input id="test" min="1" max="10" value='10' step="1" onchange="showVal(this.value)" type="range"/>-->
          
          <!--<div id="panzoom-element" style="height:500px; wdith:500px;">-->
        
          <v-card
          id="cardMap"
          height= "100%"
          style=" color: white; border: 4px solid #3B435F">
            <v-card
            id="panzoom-element"
            height="100%"
            style=" background-color: #E6E7EB; border: 1px solid #3B435F;"
            >
            <canvas id='idBlock' width='500' height='500' @click="changeColorOnClick" ></canvas>
            </v-card>
          <!--<v-img height="300px" src="/plantest.png">
          </v-img>-->
        </v-card>
        
        </v-col>
        
      </v-row>

      <v-row justify="center" style="background-color:#4b548b;">
        <v-btn
              dark
              color="#4b548b"
              style="margin-bottom:-1%; border: 1px solid #3B435F;"
              @click="displayFooter()"
            >
            <!--click="#modification_footer"-->
            <v-icon id="iconChevronDisplayFooter1" dark>
              mdi-chevron-down
            </v-icon>
            <v-icon id="iconChevronDisplayFooter2" dark style="display:none">
              mdi-chevron-up
            </v-icon>
        </v-btn>
      </v-row>
      
      <v-row id="modification_footer" style="padding: 1% 2% 0% 2%; background-color: white; border-top: 5px solid #3B435F;">
          <v-col cols="12" sm="12" md="12" lg="4" xl="4">
            <v-card-text style="font-weight: bold; color: #4b548b; font-size: 22px; ">Modification du plan</v-card-text>
          </v-col>
          <v-spacer></v-spacer>
          <v-col cols="12" sm="12" md="12" lg="2" xl="2">
            <v-btn
              fab
              dark
              color="#4b548b"
            >
              <v-icon dark>
                mdi-plus
              </v-icon>
            </v-btn>
            <v-btn
              fab
              dark
              color="#4b548b"
              style="margin-left:3%"
            >
              <v-icon dark>
                mdi-pencil
              </v-icon>
            </v-btn>
            <v-btn
              fab
              dark
              color="#4b548b"
              style="margin-left:3%"
            >
              <v-icon dark>
                mdi-delete
              </v-icon>
            </v-btn>
          </v-col>
      </v-row>
      <v-row style="padding: 2% 2% 2% 2%;">
        
        <v-col cols="12" sm="12" md="12" lg="4" xl="4">
          <v-row>
            <v-card-text style="font-size: 16px;">Nom bloc:</v-card-text>
          </v-row>
          <v-row>
            <v-text-field
            v-model="form_nom"
            solo
            label="Rayon1_fruit"
            clearable
            ></v-text-field>
          </v-row>
        </v-col>

        <v-col cols="12" sm="12" md="12" lg="4" xl="4" style="margin-left : 10%">
          <v-row>
            <v-card-text style="font-size: 16px;">Coordonnée X :</v-card-text>
          </v-row>
          <v-row>
            <v-text-field
            v-model="form_x"
            solo
            label="ex:100"
            clearable
            ></v-text-field>
          </v-row>
        </v-col>



      </v-row>
      <v-row style="padding: 0% 0% 0% 2%; margin-top:-3%;">

        <v-col cols="12" sm="12" md="12" lg="4" xl="4" >
          <v-row>
            <v-card-text style="font-size: 16px;">Type de bloc :</v-card-text>
          </v-row>
          <v-row>
            <v-select
              :items="items"
              label="Solo field"
              solo
              style="margin-top:0%;"
            ></v-select>
          </v-row>
        </v-col>

        <v-col cols="12" sm="12" md="12" lg="4" xl="4" style="margin-left : 9%">
          <v-row>
            <v-card-text style="font-size: 16px;">Coordonnée Y :</v-card-text>
          </v-row>
          <v-row>
            <v-text-field
              v-model="form_y"
              solo
              label="ex:100"
              clearable
            ></v-text-field>
          </v-row>
        </v-col>

        <v-spacer></v-spacer>

        <v-col cols="12" sm="12" md="12" lg="2" xl="2" style="margin-right:3%">
          <v-row  >
            <v-btn
                  color="#4b548b"
                  dark
                  x-large
                >
                  Ajouter au Plan
              </v-btn>
          </v-row>
        </v-col>

      </v-row>

      
      <!--<div class="center mt-15" style="background-color: black">
        <v-card>
          <v-img src="/banderole.png"> </v-img>
        </v-card>
      </div>

      <v-col>
        <v-card height="300" color="#707070" style="padding: 1%">
          <v-col>
            <v-row style="margin-bottom: 2%">
              <v-card-title style="font-weight: bold; color: white">{{
                $t("texteHeader") 
              }}</v-card-title>
            </v-row>
            <v-row style="margin-left: 2%">
              <v-text style=" color: white">{{
                $t("texteAccueil")
              }}</v-text>
            </v-row>
          </v-col>
        </v-card>
      </v-col>-->

      
    
 
  </div>
</template>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
<script>
import Panzoom from '@panzoom/panzoom'

class Rectangle {
  constructor(x, y, height, width, color){
    this.x=x;
    this.y=y;
    this.height=height;
    this.width=width;
    this.color = color;
  }

  setColor(newColor){
    this.color = newColor;
  }

  draw(context) {
    context.beginPath();
    //context.rect
    context.rect(this.x, this.y, this.height, this.width);
    context.fillStyle = this.color;
    context.fill();
    context.stroke();
    context.closePath();
  }


  clickRect(mouseX, mouseY){
    if((mouseX > this.x) && (mouseX < this.y + this.width) &&
          (mouseY > this.y) && (mouseY < this.y + this.height)){
      this.setColor("#11101d");
      return true;
    }
    else{
      return false;
    }
  }

}


/*if(typeof this.cnv !== "undefined" && this.cnv != null ){
  this.cnv.addEventListener('click',(event) => {
    console.log("test")
    let rect = this.cnv.getBoundingClientRect();
    let x= event.clientX - rect.left;
    let y= event.clientY - rect.top;
    this.blocksArray[0].clickRect(x,y)
    this.draw(this.cnv.getContext("2d"));
  });
}*/

function addToMap(iD) {
    $(iD).append("<canvas id='idBlock' width='500' height='500' v-on:click='changeColorOnClick(event)'></canvas>" );
  }
export default {
  name: "accueil",
  extend : false,
  cpt:1,
  blocksArray : [],
  //cnv : document.getElementById('idblock'),
  mounted() {
        this.panzoom = Panzoom(document.getElementById('panzoom-element'), {
            maxScale: 5
        })
        this.blocksArray = [];
    },
  methods: {
    /**
     * changes, redirects to the page
     * @param to :  name of the page to redirect
     */
    redirect(to) {
      this.$router.push(to);
    },

    zoom(level){
            level === -1 ? this.panzoom.zoomOut() : this.panzoom.zoomIn()
    },

    displayFooter(){
      if(this.extend){
        document.getElementById('mapHeader1').style.display="flex"; 
        document.getElementById('mapHeader2').style.display="flex";
        document.getElementById('iconChevronDisplayFooter1').style.display="block";
        document.getElementById('iconChevronDisplayFooter2').style.display="none";
        this.extend=false;
      }else{
        document.getElementById('mapHeader1').style.display="none";
        document.getElementById('mapHeader2').style.display="none";
        document.getElementById('iconChevronDisplayFooter1').style.display="none";
        document.getElementById('iconChevronDisplayFooter2').style.display="block";
        this.extend=true;
      }
      
    },


    addBlockToMap(){
      //addToMap();
      //@mouseover='changeT'
      //$("#panzoom-element").append("<canvas id='idBlock' width='500' height='500' ></canvas>" );
      let cnv = document.getElementById("idBlock");
      let ctx = cnv.getContext("2d");
      let r = new Rectangle(100,100,200,200, '#f56');
      this.blocksArray.push(r);
      r.draw(ctx);
      /*let ele = document.createElement("canvas");
      
      ele.setAttribute('id', 'idblock');
      ele.setAttribute('height', '500');
      ele.setAttribute('width', '500');
      this.cpt++;
      let ctx = ele.getContext("2d");
      let r = new Rectangle(100,100,200,200, '#f56');
      this.blocksArray.push(r);
      r.draw(ctx);
      */

      //let ctx = ele.getContext("2d");
      //ctx.strokeStyle = "green";
      /*ctx.strokeRect(0, 100, 100, 100);
      ctx.strokeRect(50, 100, 100, 100);
      ctx.strokeRect(200, 100, 100, 100);*/

      /*document.getElementById("panzoom-element").appendChild(ele);
      this.cnv = ele;*/

      /*ele = document.createElement("canvas");
      ele.setAttribute('id', 'idblock2');
      this.cpt++;
      ele.setAttribute('height', '300');
      ele.setAttribute('width', '300');
      this.cpt++;
      let ctx = ele.getContext("2d");
      ctx.strokeStyle = "green";
      ctx.strokeRect(0, 100, 100, 100);
      ctx.strokeRect(50, 100, 100, 100);
      document.getElementById("idblock").appendChild(ele);*/
    },

    async changeT(){
      console.log("test2");
    },

    changeColorOnClick(event){
      console.log('test');
      let cnv = document.getElementById("idBlock");
      let rect = cnv.getBoundingClientRect();
      let x= event.clientX - rect.left;
      let y= event.clientY - rect.top;
      this.blocksArray[0].clickRect(x,y)
      this.blocksArray[0].draw(cnv.getContext("2d"));
    },

    setZoom(zoom,el) {
      
      let transformOrigin = [0,0];
      //el = el || instance.getContainer();
      let p = ["webkit", "moz", "ms", "o"];
      let s = "scale(" + zoom + ")";
      let oString = (transformOrigin[0] * 100) + "% " + (transformOrigin[1] * 100) + "%";

      for (let i = 0; i < p.length; i++) {
          el.style[p[i] + "Transform"] = s;
          el.style[p[i] + "TransformOrigin"] = oString;
      }

      el.style["transform"] = s;
      el.style["transformOrigin"] = oString;
      
    },

//setZoom(5,document.getElementsByClassName('container')[0]);

    showVal(a){
      var zoomScale = Number(a)/10;
      this.setZoom(zoomScale,document.getElementById('mapSpace'))
    },

  },
  data: () => ({
      items: ['Foo', 'Bar', 'Fizz', 'Buzz'],
  }),
};
</script>

<style>
  #mapSpace{
    transform: scale(0.1);
    transform-origin: 0% 0% 0px;
  }
</style>


