<template>
  <div id="main">

      <v-row style="padding: 2% 2% 0% 2%; background-color:#4b548b;"> <!--#f5f2f2  #E6E7EB-->
        <v-card-title style=" color: white; font-size: 22px; margin-right:-2%" >
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
        
          
          <v-btn large rounded color="#11101d" @click="zoomIn()"> <!--  zoom(1)-->
            <v-icon size="28" style="color: white;" >
                mdi-magnify-plus-outline
            </v-icon> 
          </v-btn>
          <v-btn large rounded color="#11101d" @click="zoomOut()"> <!-- zoom(-1) -->
            <v-icon size="28" style="color: white">
                mdi-magnify-minus-outline
            </v-icon>
          </v-btn>
          <v-btn @click="addBlockToMap()">bnbnbn</v-btn>
        
        
      </v-row>
      <v-row id="mapHeader2"  justify="center" style="padding: 0% 2% 2% 2%; background-color:#4b548b; height:550px; z-index:2">
        <v-col  cols="6" sm="6" md="8" lg="7" xl="7" >
          
          <!--<input id="test" min="1" max="10" value='10' step="1" onchange="showVal(this.value)" type="range"/>-->
          
          <!--<div id="panzoom-element" style="height:500px; wdith:500px;">-->
        
          
           
          <!--<v-card
          id="cardMap"
          height= "100%"
          
          style=" color: white; border: 4px solid #3B435F; position:relative">-->
            <!--<div
            id="wrapper"
            
            style=" background-color: black; height:500px; width:100% border: 1px solid #3B435F; position:relative" 
            >-->
            <canvas id='idBlock' height='500' width='1000' @mousedown="mouseDown" @mouseup ="mouseUp" @mouseover="mouseOver" @mouseout="mouseOut" @mousemove="mouseMove" style="border: 4px solid #3B435F; background-color: white; position:absolute " ></canvas>
           
            <!-- #E6E7EB  panzoom-element-->
            <!--<canvas id='idBlock' width='1000' height='1000' @mousemove="changeColorOnClick2" @click="changeColorOnClick" style="border: 4px solid #3B435F; position: absolute;" ></canvas>-->
            <!--</div>-->
          <!--<v-img height="300px" src="/plantest.png">
          </v-img>-->
        <!--</v-card>-->
        
        </v-col>
        <v-col cols="6" sm="6" md="4" lg="5" xl="5" style="z-index:2"> 
          <v-card id="cardLayoutDetails" height="100%" width="100%" style="color:white; ">
            <v-row>
              <v-col style="margin-top: -12px; margin-bottom:-8%">
                <v-img gradient="to top right, rgba(100,115,201,.13), rgba(25,32,72,.6)" class="rounded" height="90%" width="100%" src="/laitier.jpg" style="">
                <v-row  style="">
                  <v-col  cols="6" sm="6" md="5" lg="5" xl="5" style="margin-left:12px; margin-top:12px">
                  <v-avatar size="100" color="primary" >
                    <v-avatar size = "95">
                      <v-img placeholder src="/icon_laitier.jpg">
                      </v-img>
                    </v-avatar>
                  </v-avatar>
                  </v-col>
                  <v-spacer></v-spacer>
                  <v-col cols="4" sm="3" md="3" lg="2" xl="2" >
                    <v-btn
                      color="white"
                      icon
                      large
                      @click="closeLayoutDetails()"
                    >
                      <v-icon>mdi-close</v-icon>
                    </v-btn>
                  </v-col>
                </v-row>
                </v-img>
              </v-col>

              <v-row style="margin-left:1%">
                <v-col>
                  <v-card-title style="color:black">
                    Rayon produits laitiers  
                    <span style="color:transparent"> 
                      _
                    </span> 
                    <span style="color:grey; font-size:15px"> 
                      #block1
                    </span>
                  </v-card-title> 
                </v-col>
              </v-row>

              <v-row style="margin-left:1%; margin-bottom:5%">
                <v-col style="color:black">
                  <v-row>
                    <v-col>
                      <v-card-text style="font-size:16px" >
                        Statistiques du rayon : 
                      </v-card-text>
                    </v-col>
                  </v-row>
                  <v-row align="center">
                    <v-col cols="4" sm="3" md="3" lg="1" xl="1" style="margin-top:-12px; margin-left:12px; margin-right:-12px;">
                      <v-icon size="30" color="#4b548b">
                        mdi-podium-gold
                      </v-icon>
                    </v-col>
                    <v-col>
                      <v-card-text >
                        Article en tendance du rayon: #referenceMarque
                      </v-card-text>
                    </v-col>
                  </v-row>

                   <v-row align="center">
                    <v-col cols="4" sm="3" md="3" lg="1" xl="1" style="margin-top:-12px; margin-left:12px; margin-right:-12px;">
                      <v-icon size="30" color="#4b548b">
                        mdi-clock-time-two-outline
                      </v-icon>
                    </v-col>
                    <v-col>
                      <v-card-text >
                        Temps passé en moyenne: #tempsPassé
                      </v-card-text>
                    </v-col>
                  </v-row>

                  <v-row align="center" justify="end">
                    <v-col cols="12" sm="9" md="7" lg="4" xl="4" style="margin-top:-10px; ">
                      <v-btn
                        text
                        color="primary"
                        style="font-size:15px"
                      >
                        Voir Plus
                      </v-btn>
                    </v-col>
                  </v-row>
                  
                </v-col>
              </v-row>

            </v-row>
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
      
      <v-row id="modification_footer" style="padding: 1% 2% 0% 2%; background-color: white; border-top: 5px solid #3B435F; ">
          <v-col cols="12" sm="12" md="12" lg="4" xl="4">
            <v-card-text style="font-weight: bold; color: #4b548b; font-size: 22px; ">Modification du plan</v-card-text>
          </v-col>
          <v-spacer></v-spacer>
          <v-col cols="12" sm="12" md="12" lg="2" xl="2" style="z-index:1">
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
              style="margin-left:3%;"
            >
              <v-icon dark>
                mdi-pencil
              </v-icon>
            </v-btn>
            <v-btn
              fab
              dark
              color="#4b548b"
              style="margin-left:3%;"
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

class Beacon {
  constructor(x, y, radius, color, lineColor, lineWidth){
    this.x=x;
    this.y=y;
    this.radius=radius;
    this.color=color;
    this.lineColor=lineColor;
    this.lineWidth = lineWidth;
  }

  setColor(newColor, newLineColor, newlineWidth){
    this.color = newColor;
    this.lineColor = newLineColor;
    this.lineWidth = newlineWidth;
  }

  setBeaconAtScale(newX, newY, newRadius){
    this.x=newX;
    this.y=newY;
    this.radius=newRadius;
  }

  draw2(context) {
    context.beginPath();
    context.arc(this.x,this.y,this.radius,0*Math.PI,2*Math.PI);
    context.closePath()
    context.fillStyle = this.color;
    context.fill();
    context.strokeStyle = this.lineColor;
    context.stroke();
  }


  clickBeacon(mouseX, mouseY){
    if( Math.pow((mouseX - this.x),2) + Math.pow((mouseY - this.y),2) <= Math.pow(this.radius,2)){
      this.setColor("#63e063", '#1b1c1b', 5);
      return true;
    }
    else{
      this.setColor('#32a852', '#1b1c1b', 2);
      return false;
    }
  }

}

class Rectangle {
  constructor(x, y, height, width, color, lineColor, lineWidth){
    this.x=x;
    this.y=y;
    this.height=height;
    this.width=width;
    this.color = color;
    this.lineColor = lineColor;
    this.lineWidth = lineWidth;
  }

  setColor(newColor, newLineColor, lineWidth){
    this.color = newColor;
    this.lineColor = newLineColor;
    this.lineWidth = lineWidth;
  }

  setRectAtScale(newX, newY, newHeight, newWidth){
    this.x=newX;
    this.y=newY;
    this.height=newHeight;
    this.width=newWidth;
  }

  draw(context) {
    context.beginPath();
    //context.rect
    context.rect(this.x, this.y, this.height, this.width);
    context.fillStyle = this.color;
    context.fill();
    
    context.strokeStyle = this.lineColor;
    context.lineWidth = this.lineWidth;
    context.stroke();
    context.closePath();
  }

  draw2(context) {
    
    context.beginPath();
    context.rect(this.x, this.y, this.width, this.height);
    context.closePath()
    context.fillStyle = this.color;
    context.fill();
    
    context.strokeStyle = this.lineColor;
    context.lineWidth = this.lineWidth;
    context.stroke();
    
    
  }


  clickRect(mouseX, mouseY){
    if((mouseX > this.x) && (mouseX < this.x + this.width) &&
          (mouseY > this.y) && (mouseY < this.y + this.height) && this.color!="#E6E7EB" && this.color!="#bf573f"){
      this.setColor("#323D71", "#4DDFAF", 5);
      return true;
    }
    if(this.color!="#E6E7EB" && this.color!="#bf573f"){
      this.setColor("#91A0FF", "#4B548B", 2);
      return false;
    }
    if(this.color=="#E6E7EB"){
      this.setColor("#E6E7EB", "#4B548B", 2);
      return false;
    }

    if(this.color!="#bf573f"){
      this.setColor("#bf573f", "#4B548B", 2);
      return false;
    }
  }

}

export default {
  name: "accueil",
  extend : false,
  cpt:1,
  blocksArray : [],
  beaconArray : [],
  vueCanvas:null,
  vueCanvasPreviousSize : [],
  scale: 1.0,
  translatePos : {},
  scaleMultiplier : 0.8,
  startDragOffset : {},
  vectorMove : {},
  mouseDown : false,
  mouseUp : false,
  canvas:null,
  //cnv : document.getElementById('idblock'),
  mounted() {
        //this.panzoom = Panzoom(document.getElementById('panzoom-element'), {
        //    maxScale: 5
        //})
        let canvas = document.getElementById("idBlock");
        this.canvas = canvas;
        //let panzoomElement = document.getElementById("panzoom-element");
        let ctx = canvas.getContext("2d");  
        this.vueCanvas = ctx;
        this.blocksArray = [];
        this.beaconArray = [];
        this.vueCanvasPreviousSize = [canvas.getBoundingClientRect().left, canvas.getBoundingClientRect().top, (canvas.getBoundingClientRect().bottom-canvas.getBoundingClientRect().top), (canvas.getBoundingClientRect().right-canvas.getBoundingClientRect().left)];
        //let l = document.getElementById("panzoom-element").style.transform.split(" ")[0];
        //let l2 = l.replace('scale(', '');
        //this.scale = l2.replace(')', '');
        this.scale = 1.0;
        this.scaleMultiplier = 0.8;
        this.startDragOffset = {
          x: 0.0,
          y: 0.0
        };

        this.translatePos = {
          x: 0.0,
          y: 0.0
        };

        this.vectorMove = {
          previousX: canvas.getBoundingClientRect().left,
          previousY: canvas.getBoundingClientRect().top,
          actualX: canvas.getBoundingClientRect().left,
          actualY: canvas.getBoundingClientRect().top
        };
      

    },
  methods: {
    /**
     * changes, redirects to the page
     * @param to :  name of the page to redirect
     */
    redirect(to) {
      this.$router.push(to);
    },

    /*zoom(level){
      if(level === -1){
        
        this.panzoom.zoomOut()
        for (let i=0; i<this.blocksArray.length; i++){
          console.log(this.scale)
          let s = ((746/1000))
          this.blocksArray[i].setRectAtScale(this.blocksArray[i].x, this.blocksArray[i].y,  s*this.blocksArray[i].height, s*this.blocksArray[i].width);
          this.blocksArray[i].draw(this.vueCanvas);
          console.log(this.blocksArray[i].x, this.blocksArray[i].y, this.blocksArray[i].height, this.blocksArray[i].width);
        }
        this.scale=(746/1000);
        
      }
      else{
        this.panzoom.zoomIn()
        //Math.sqrt(1.35/1)
        for (let i=0; i<this.blocksArray.length; i++){
          console.log(this.scale)
          let s = ((1360/1000))
          this.blocksArray[i].setRectAtScale(this.blocksArray[i].x, this.blocksArray[i].y,  s*this.blocksArray[i].height, s*this.blocksArray[i].width);
          
          //this.blocksArray[i].setRectAtScale((1360/1000)*this.blocksArray[i].x, (1360/1000)*this.blocksArray[i].y,  (1360/1000)*this.blocksArray[i].height, (1360/1000)*this.blocksArray[i].width);
          this.blocksArray[i].draw(this.vueCanvas);
          console.log(this.blocksArray[i].x, this.blocksArray[i].y, this.blocksArray[i].height, this.blocksArray[i].width);
        }
        this.scale=(1360/1000);
      }
      let l = document.getElementById("panzoom-element").style.transform.split(" ")[0];
      let actualScale = l.replace('scale(', '');

    },*/

    reDrawingCanva(){
      this.vueCanvas.clearRect(0, 0, this.canvas.width, this.canvas.height);
      this.vueCanvas.save();
      this.vueCanvas.translate(this.translatePos.x, this.translatePos.y);
      //this.vueCanvas.scale(this.scale, this.scale);
      for (let i=0; i<this.blocksArray.length; i++){
          //this.blocksArray[i].setRectAtScale(this.blocksArray[i].x, this.blocksArray[i].y,  s*this.blocksArray[i].height, s*this.blocksArray[i].width);
          this.blocksArray[i].setRectAtScale(this.blocksArray[i].x, this.blocksArray[i].y, this.blocksArray[i].height, this.blocksArray[i].width)
          this.blocksArray[i].draw2(this.vueCanvas);
          //console.log(this.blocksArray[i].x, this.blocksArray[i].y, this.blocksArray[i].height, this.blocksArray[i].width);
      }
      for (let i=0; i<this.beaconArray.length; i++){
          //this.blocksArray[i].setRectAtScale(this.blocksArray[i].x, this.blocksArray[i].y,  s*this.blocksArray[i].height, s*this.blocksArray[i].width);
          this.beaconArray[i].setBeaconAtScale(this.beaconArray[i].x, this.beaconArray[i].y, this.beaconArray[i].radius)
          this.beaconArray[i].draw2(this.vueCanvas);
          //console.log(this.blocksArray[i].x, this.blocksArray[i].y, this.blocksArray[i].height, this.blocksArray[i].width);
      }
      this.vueCanvas.restore();
    },

    reDrawing(){
      
      //this.vueCanvas.scale(this.scale, this.scale);
      this.blocksArray[0].draw2(this.vueCanvas);
    },

    zoomIn(){
      console.log("zoomin")
      console.log(this.scale)
      this.scale = this.scale / this.scaleMultiplier;
      //this.reDrawingCanva();

      if(this.scale>=1){
        for (let i=0; i<this.blocksArray.length; i++){
          //this.blocksArray[i].setRectAtScale(this.blocksArray[i].x, this.blocksArray[i].y,  s*this.blocksArray[i].height, s*this.blocksArray[i].width);
          this.blocksArray[i].setRectAtScale(this.blocksArray[i].x*this.scale, this.blocksArray[i].y*this.scale, this.blocksArray[i].height*this.scale, this.blocksArray[i].width*this.scale);
        }
        for (let i=0; i<this.beaconArray.length; i++){
          //this.blocksArray[i].setRectAtScale(this.blocksArray[i].x, this.blocksArray[i].y,  s*this.blocksArray[i].height, s*this.blocksArray[i].width);
          this.beaconArray[i].setBeaconAtScale(this.beaconArray[i].x*this.scale, this.beaconArray[i].y*this.scale, this.beaconArray[i].radius*this.scale)
        }
      }
      else {
        for (let i=0; i<this.blocksArray.length; i++){
          //this.blocksArray[i].setRectAtScale(this.blocksArray[i].x, this.blocksArray[i].y,  s*this.blocksArray[i].height, s*this.blocksArray[i].width);
          this.blocksArray[i].setRectAtScale(this.blocksArray[i].x/this.scale, this.blocksArray[i].y/this.scale, this.blocksArray[i].height/this.scale, this.blocksArray[i].width/this.scale);
          
        }
        for (let i=0; i<this.beaconArray.length; i++){
          this.beaconArray[i].setBeaconAtScale(this.beaconArray[i].x/this.scale, this.beaconArray[i].y/this.scale, this.beaconArray[i].radius/this.scale)
        }  
      }
      this.reDrawingCanva();

    
    },

    zoomOut(){
       this.scale = this.scale * this.scaleMultiplier;

      if(this.scale<1){
        for (let i=0; i<this.blocksArray.length; i++){
          console.log(this.scale);
          this.blocksArray[i].setRectAtScale(this.blocksArray[i].x*this.scale, this.blocksArray[i].y*this.scale, this.blocksArray[i].height*this.scale, this.blocksArray[i].width*this.scale);
          
        }
        for (let i=0; i<this.beaconArray.length; i++){
          this.beaconArray[i].setBeaconAtScale(this.beaconArray[i].x*this.scale, this.beaconArray[i].y*this.scale, this.beaconArray[i].radius*this.scale)
          
        }
      }
      else {
        for (let i=0; i<this.blocksArray.length; i++){
          //this.blocksArray[i].setRectAtScale(this.blocksArray[i].x, this.blocksArray[i].y,  s*this.blocksArray[i].height, s*this.blocksArray[i].width);
          this.blocksArray[i].setRectAtScale(this.blocksArray[i].x/this.scale, this.blocksArray[i].y/this.scale, this.blocksArray[i].height/this.scale, this.blocksArray[i].width/this.scale);
        }

        for (let i=0; i<this.beaconArray.length; i++){
          this.beaconArray[i].setBeaconAtScale(this.beaconArray[i].x/this.scale, this.beaconArray[i].y/this.scale, this.beaconArray[i].radius/this.scale)
          
        }
         
      }
      
      this.reDrawingCanva();
      
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
      //$("#panzoom-element").append("<canvas id='idBlock' width='500' height='500' ></canvas>" );
      let mapBackground = new Rectangle(0.0,0.0,3000.0,2000.0, '#E6E7EB', '#4B548B', 2);
      this.blocksArray.push(mapBackground);
      let entrance = new Rectangle(0.0,400.0,50.0,20.0, '#bf573f', '#4B548B', 2);
      this.blocksArray.push(entrance);
      this.blocksArray.push(new Rectangle(100.0,100.0,100.0,200.0, '#91A0FF', '#4B548B', 2));
      this.blocksArray.push(new Rectangle(300.0,100.0,100.0,300.0, '#91A0FF', '#4B548B', 2));
      this.blocksArray.push(new Rectangle(800.0,700.0,100.0,300.0, '#91A0FF', '#4B548B', 2));
      this.beaconArray.push(new Beacon(100, 75, 15, '#32a852', '#1b1c1b', 2));
      this.reDrawingCanva();

    },

    changeBlocksSize(previousSize, actualSize){
      //let cnv = document.getElementById("panzoom-element").getBoundingClientRect();
      for (let i=0; i<this.blocksArray.length; i++){
        //this.blocksArray[i].setRectAtScale((actualSize[0]/previousSize[0])*this.blocksArray[i].x, (actualSize[1]/previousSize[1])*this.blocksArray[i].y, (actualSize[2]/previousSize[2])*this.blocksArray[i].height, (actualSize[3]/previousSize[3])*this.blocksArray[i].width);
        //this.blocksArray[i].setRectAtScale((actualSize[3]/previousSize[3])*this.blocksArray[i].x, (actualSize[2]/previousSize[2])*this.blocksArray[i].y, (actualSize[2]/previousSize[2])*this.blocksArray[i].height, (actualSize[3]/previousSize[3])*this.blocksArray[i].width);
        /*let l = document.getElementById("panzoom-element").style.transform.split(" ")[0];
        let l2 = l.replace('scale(', '');
        let scale = l2.replace(')', '');
        */
       console.log(this.scale)
        this.blocksArray[i].setRectAtScale(parseFloat(this.scale)*this.blocksArray[i].x, parseFloat(this.scale)*this.blocksArray[i].y,  parseFloat(this.scale)*this.blocksArray[i].height, parseFloat(this.scale)*this.blocksArray[i].width);
        this.blocksArray[i].draw(this.vueCanvas);
        console.log(this.blocksArray[i].x, this.blocksArray[i].y, this.blocksArray[i].height, this.blocksArray[i].width);
      }
    },

    changeT(){
      console.log("test2");
    },



    changeColorOnClick(event){
      console.log('test');
      let cnv = document.getElementById("idBlock");
      let rect = cnv.getBoundingClientRect();
      let x= event.clientX - rect.left;
      let y= event.clientY - rect.top;
      for (let i=0; i<this.blocksArray.length; i++) {
        this.blocksArray[i].clickRect(x,y)
        this.blocksArray[i].draw(cnv.getContext("2d"));
      }
    },

    changeColorOnClick2(event){
      console.log('test');
      let cnv = document.getElementById("idBlock");
      let rect = cnv.getBoundingClientRect();
      let x= event.clientX - rect.left;
      let y= event.clientY - rect.top;

    

      for (let i=0; i<this.blocksArray.length; i++){
        if(this.blocksArray[i].clickRect(x,y)){
          
          this.reDrawingCanva();
        }
        //this.blocksArray[i].draw2(cnv.getContext("2d"));
        
      }
      
    },


      mouseDown(event) {
        console.log("mousedown");
        this.mouseDown = true;
        this.startDragOffset.x = event.clientX - this.translatePos.x;
        this.startDragOffset.y = event.clientY - this.translatePos.y;
        this.vectorMove.previousX= this.vectorMove.actualX;
        this.vectorMove.previousY= this.vectorMove.actualY;
        /*for (let i=0; i<this.blocksArray.length; i++){
          this.blocksArray[i].setRectAtScale(this.blocksArray[i].x+(this.translatePos.x*scale), this.blocksArray[i].y+(this.translatePos.y*scale),  this.blocksArray[i].height, this.blocksArray[i].width);
        }*/
      },

      mouseUp(event) {
        this.mouseDown = false;
        if(this.vectorMove.previousX != this.vectorMove.actualX){
          for (let i=0; i<this.blocksArray.length; i++){
              console.log(event.clientX)
              this.blocksArray[i].setRectAtScale(this.blocksArray[i].x + this.translatePos.x, this.blocksArray[i].y + this.translatePos.y ,  this.blocksArray[i].height, this.blocksArray[i].width);
              
          }
          for (let i=0; i<this.beaconArray.length; i++){
              console.log(event.clientX)
              this.beaconArray[i].setBeaconAtScale(this.beaconArray[i].x + this.translatePos.x, this.beaconArray[i].y + this.translatePos.y , this.beaconArray[i].radius)
          
          }
          
        }
      },

      mouseOver(event){
        this.mouseDown = false;
      },

      mouseOut(event) {
        this.mouseDown = false;
      },

      mouseMove(event) {
        if (this.mouseDown) {
          console.log(this.startDragOffset.x, this.translatePos.x)
          this.translatePos.x = event.clientX - this.startDragOffset.x;
          this.translatePos.y = event.clientY - this.startDragOffset.y;
          

          console.log(this.translatePos)
          //this.reDrawingCanva();
          let cnv = document.getElementById("idBlock");
          let rect = cnv.getBoundingClientRect();
          this.vectorMove.actualX=this.translatePos.x;
          this.vectorMove.actualY=this.translatePos.y;
          console.log("translate "+ this.translatePos.x, this.translatePos.y)
          console.log("drag "+ this.startDragOffset.x, this.startDragOffset.y)
          console.log("vector "+ this.vectorMove.actualX, this.vectorMove.actualY, this.vectorMove.previousX, this.vectorMove.previousY)
          for (let i=0; i<this.blocksArray.length; i++){
            //this.blocksArray[i].setRectAtScale(this.blocksArray[i].x + (this.vectorMove.actualX- (this.blocksArray[i].x)), this.blocksArray[i].y + (this.vectorMove.actualY- (this.blocksArray[i].y)),  this.blocksArray[i].height, this.blocksArray[i].width);
            this.blocksArray[i].setRectAtScale(this.blocksArray[i].x, this.blocksArray[i].y,  this.blocksArray[i].height, this.blocksArray[i].width);
          
          }
          for (let i=0; i<this.beaconArray.length; i++){
            this.beaconArray[i].setBeaconAtScale(this.beaconArray[i].x, this.beaconArray[i].y, this.beaconArray[i].radius)
          }
        }
        if(!this.mouseDown){
          let cnv = document.getElementById("idBlock");
          let rect = cnv.getBoundingClientRect();
          let x= event.clientX - rect.left;
          let y= event.clientY - rect.top;
          for (let i=0; i<this.blocksArray.length; i++){
            this.blocksArray[i].clickRect(x,y)
            //this.blocksArray[i].draw2(cnv.getContext("2d"));
          }
          for (let i=0; i<this.beaconArray.length; i++){
            this.beaconArray[i].clickBeacon(x,y)
          }
        }

        this.reDrawingCanva();
        
      },
    
    closeLayoutDetails(){
      document.getElementById("cardLayoutDetails").style.display="none";
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


