<template>
  <div class="masthead">
    <b-container>
      <b-navbar toggleable type="dark">
        <b-navbar-brand to="/">
            <svg version="1.1" id="icon__logo" class="icon__logo" xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="95px" height="40px" viewBox="0 0 95 40" enable-background="new 0 0 95 40" xml:space="preserve">
                <path d="M9.051,19.953l-2.033-5.348l-5.497-1.978c-0.843-0.303-1.411-1.09-1.411-1.966c0-0.875,0.568-1.664,1.411-1.967l5.494-1.976 L9.052,1.37C9.36,0.55,10.178,0,11.075,0c0.897,0,1.708,0.55,2.022,1.369l2.014,5.305l5.682,2.096 c0.756,0.345,1.242,1.086,1.242,1.89c0,0.657-0.336,1.261-0.87,1.653l-0.177-0.472L12.887,8.88l-1.812-4.815L9.261,8.881 l-4.895,1.78c0,0,4.651,1.688,4.895,1.777c0.089,0.243,1.815,4.82,1.815,4.82l1.448-3.845l2.693,0.971l-2.12,5.57 c-0.314,0.819-1.125,1.37-2.022,1.37C10.178,21.324,9.36,20.773,9.051,19.953"></path>
                <path d="M24.225,1.379l2.033,5.348l5.497,1.978c0.843,0.303,1.411,1.09,1.411,1.966c0,0.875-0.568,1.664-1.411,1.967l-5.494,1.976 l-2.037,5.348c-0.309,0.819-1.127,1.369-2.024,1.369s-1.708-0.55-2.021-1.369l-2.016-5.305l-5.683-2.096 c-0.755-0.345-1.241-1.086-1.241-1.89c0-0.657,0.338-1.261,0.87-1.653l0.177,0.472l8.101,2.961l1.812,4.816l1.815-4.816l4.895-1.78 c0,0-4.651-1.688-4.895-1.777c-0.089-0.243-1.815-4.82-1.815-4.82L20.752,7.92l-2.694-0.97l2.121-5.571 c0.313-0.819,1.123-1.37,2.021-1.37S23.915,0.56,24.225,1.379"></path>
                <path d="M44.519,20.546c-1.611-0.628-2.846-0.887-4.455-0.887c-4.616,0-7.73,3.233-7.73,8.14c0,4.386,1.825,7.673,7.352,7.673h4.833 L44.519,20.546 M49.295,39.386H39.152c-7.194,0-11.701-4.749-11.701-12.267c0-6.784,4.987-11.639,12.022-11.639 c1.61,0,3.11,0.259,5.045,0.938v-9.69h4.776L49.295,39.386L49.295,39.386z"></path>
                <path d="M77.823,35.472h4.831c5.53,0,7.354-3.288,7.354-7.673c0-4.906-3.114-8.141-7.73-8.141c-1.609,0-2.841,0.259-4.455,0.887 L77.823,35.472 M73.047,6.728h4.776v9.691c1.935-0.679,3.436-0.938,5.045-0.938c7.031,0,12.022,4.853,12.022,11.639 c0,7.518-4.509,12.267-11.701,12.267H73.047V6.728z"></path>
                <path d="M68.664,21.465c-2.774-1.789-5.386-2.548-7.215-2.548c-2.001,0-3.335,0.925-3.277,2.223 c0.138,3.053,11.497,5.598,11.657,11.707C69.94,37.127,66.332,40,61.615,40c-3.052,0-5.44-0.595-8.66-2.222v-5.201 c3.22,2.165,6.161,3.194,8.158,3.194c2.001-0.105,3.665-1.029,3.665-2.763c0-3.359-11.657-5.147-11.657-11.706 c0-4.12,3.22-6.613,8.215-6.613c2.331,0,4.718,0.65,7.327,2.006L68.664,21.465"></path>
            </svg>
        </b-navbar-brand>
        <b-navbar-brand to="/" class="divider-vertical-left pl-3">
          Dashbord
        </b-navbar-brand>
        <b-navbar-brand to="/search" class="divider-vertical-left pl-3">
          Søk
        </b-navbar-brand>
        <!--<b-navbar-brand to="/report" class="divider-vertical-left pl-3">
          Rapport
        </b-navbar-brand>-->
      </b-navbar>
    </b-container>
  </div>
</template>

<script>
export default {
  name: 'NavBar'
};
</script>

<style scoped lang="scss">
@import '~bootstrap/scss/bootstrap';
@import '../assets/main';

.masthead {
  background-color: $white;
  border-bottom: 1px solid $gray-500;
  a.navbar-brand {
    color: $gray-700;
  }
  a.navbar-brand:hover {
    color: $bris-color;
  }
  a.navbar-brand:active {
    color: $bris-color;
  }
  a.navbar-brand:focus {
    color: $bris-color;
  }
}
</style>
