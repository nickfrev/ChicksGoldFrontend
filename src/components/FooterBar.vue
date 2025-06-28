<script setup lang="ts">
import IconChicksGoldLogo from './icons/IconChicksGoldLogo.vue'
import IconFacebook from './icons/IconFacebook.vue'
import IconInstagram from './icons/IconInstagram.vue'
import IconTwitter from './icons/IconTwitter.vue'
import IconYoutube from './icons/IconYoutube.vue'
import StarBoxIcon from 'vue-material-design-icons/StarBox.vue'
</script>

<template>
  <div class="footer">
    <div class="topBanner">
      <div class="centerSizer">
        <img src="@/assets/images/acceptedPayment.png" alt="Accepted Payment" />
      </div>
    </div>
    <div class="socials centerSizer">
      <div href="#"><IconFacebook /></div>
      <div href="#"><IconInstagram /></div>
      <div href="#"><IconTwitter /></div>
      <div href="#"><IconYoutube /></div>
    </div>
    <div class="container centerSizer">
      <div class="item-column-ends">
        <IconChicksGoldLogo />
        <div class="contactEmail">
          <a href="mailto:support@chicksgold.com">support@chicksgold.com</a>
        </div>
      </div>
      <div class="item-column-center">
        <h3>Chicks Gold</h3>
        <div><a href="#">Games</a></div>
        <div><a href="#">About Us</a></div>
        <div><a href="#">Blog</a></div>
        <div><a href="#">Site Map</a></div>
      </div>
      <div class="item-column-center">
        <h3>Support</h3>
        <div><a href="#">Contact Us</a></div>
        <div><a href="#">FAQ</a></div>
      </div>
      <div class="item-column-center">
        <h3>Legal</h3>
        <div><a href="#">Privacy Policy</a></div>
        <div><a href="#">Terms of Service</a></div>
        <div><a href="#">Copywrite Policy</a></div>
      </div>
      <div class="item-column-ends">
        <div class="stars">
          <StarBoxIcon />
          <StarBoxIcon />
          <StarBoxIcon />
          <StarBoxIcon />
          <StarBoxIcon />
        </div>
        <a class="trustPilotLink" href="#">Trustpilot Reviews</a>
      </div>
    </div>
    <div class="copywrite">
      <span>© 2017 - 2020 Chicksgold.com. All rights reserved</span>
    </div>
  </div>
</template>

<style scoped>
.footer {
  width: 100%;
  background-color: #303141;
  color: white;
}

.centerSizer {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.topBanner {
  height: 100px;
  background-color: #2b2c3b;
  margin-top: 4px;
  padding-top: 8px;
}

.copywrite {
  color: #b2b3b8;
  font-size: 0.97rem;
  font-weight: 500;
  padding: 10px;
  text-align: center;
  margin-bottom: 20px;
}

.container {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  flex-wrap: wrap;
  padding-top: 60px;
  padding-bottom: 50px;
  border-top: 1px solid #4c6085;
  color: #8f909a;
}

.item-column-ends {
  flex-basis: 23%;
  display: inline-block;
}

.item-column-center {
  flex-basis: 18%;
  display: inline-block;
  padding: 0 20px;
}

.item-column-center > div {
  padding: 8px 0;
  font-size: 0.85rem;
  font-weight: 300;
}

.contactEmail {
  font-size: 0.9rem;
  color: #fafcff;
  margin-top: 20px;
}

h3 {
  color: white;
  font-size: 1.1rem;
  font-weight: 600;
  margin-bottom: 13px;
}

.stars {
  margin-left: 10px;
  color: #00b67a;
  display: inline-block;
}

.stars > span {
  margin: 0 -2px;
}

.start > a {
  color: #fafcff;
}

.trustPilotLink {
  vertical-align: 6px;
  padding-left: 3px;
  color: #c0c0c5;
}

.socials > div {
  display: inline-block;
  margin: 40px 5px;
  cursor: pointer;
}

.socials > div:hover {
  color: #8b8b8b;
}

@media (width <= 1000px) {
  .item-column-ends {
    order: 1;
    flex-basis: 50%;
    text-align: center;
    margin-bottom: 40px;
  }

  .item-column-center {
    order: 2;
    flex-basis: 33%;
  }
}
</style>
