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

      <v-row justify="center" style="padding: 1% 2% 2% 2%; background-color:#4b548b; height:400px">
        <v-col cols="12" sm="12" md="12" lg="11" xl="11">
          <v-card 
          height="100%"
          style=" color: white; border: 4px solid #3B435F">
          <v-img height="300px" src="/plantest.png">
          </v-img>
        </v-card>
        </v-col>
      </v-row>

      <v-row justify="center" style="background-color:#4b548b;">
        <v-btn
              dark
              color="#4b548b"
              style="margin-bottom:-1%; border: 1px solid #3B435F;"
              
            >
            <!--click="#modification_footer"-->
            <v-icon dark>
              mdi-chevron-down
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

        <v-col cols="12" sm="12" md="12" lg="2" xl="2" style="padding :0% 15% 0% 0%">
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

<script>
export default {
  name: "accueil",
  methods: {
    /**
     * changes, redirects to the page
     * @param to :  name of the page to redirect
     */
    redirect(to) {
      this.$router.push(to);
    },
  },
  data: () => ({
      items: ['Foo', 'Bar', 'Fizz', 'Buzz'],
  }),
};
</script>

<style>
</style>


