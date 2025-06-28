<script setup lang="ts">
import IconChicksGoldLogo from './icons/IconChicksGoldLogo.vue'
import DropDown from './DropDown.vue'
import VerticalBar from './VerticalBar.vue'
import SignInButton from './SignInButton.vue'
import ShoppingCart from './ShoppingCart.vue'
</script>

<template>
  <div class="headerbar">
    <div class="logo">
      <IconChicksGoldLogo />
    </div>
    <VerticalBar class="bar" />
    <div class="right-section">
      <DropDown
        title="CURRENCY"
        :options="[
          { value: 'usd', label: 'USD', default: true },
          { value: 'eur', label: 'EUR' },
          { value: 'gbp', label: 'GBP' },
        ]"
      />
      <ShoppingCart />
      <SignInButton></SignInButton>
    </div>
    <div class="dropdowns">
      <DropDown
        title="CURRENCY"
        :options="[
          {},
          { value: 'usd', label: 'USD' },
          { value: 'eur', label: 'EUR' },
          { value: 'gbp', label: 'GBP' },
        ]"
      />
      <DropDown
        title="ITEMS"
        :options="[
          { value: 'gold', label: 'Gold' },
          { value: 'silver', label: 'Silver' },
          { value: 'bronze', label: 'Bronze' },
        ]"
      />
      <DropDown
        title="ACCOUNTS"
        :options="[
          { value: 'personal', label: 'Personal' },
          { value: 'business', label: 'Business' },
          { value: 'premium', label: 'Premium' },
        ]"
      />
      <DropDown
        title="SERVICES"
        :options="[
          { value: 'consulting', label: 'Consulting' },
          { value: 'support', label: 'Support' },
          { value: 'development', label: 'Development' },
        ]"
      />
      <DropDown
        title="SWAP"
        :options="[
          { value: 'google', label: 'Google.com', href: 'https://www.google.com/' },
          { value: 'youtube', label: 'Youtube.com', href: 'https://www.youtube.com/' },
          {
            value: 'chicksgold',
            label: 'Chicksgold.com',
            icon: '🐥',
            href: 'https://chicksgold.com/',
          },
        ]"
      />
      <DropDown
        title="SELL"
        :options="[
          { value: 'dog', label: 'Dog', icon: '🐶' },
          { value: 'hamster', label: 'Hamster', icon: '🐹' },
          { value: 'chicken', label: 'Chicken', icon: '🐔' },
          { value: 'fish', label: 'Fish', icon: '🐟' },
          { value: 'snake', label: 'Snake', icon: '🐍' },
        ]"
      />
    </div>
  </div>
</template>

<style scoped>
.headerbar {
  position: relative;
  display: flex;
  flex-wrap: wrap;
  vertical-align: middle;
  background: #303141;
  padding: 25px 20px 15px 20px;
  margin: 0px;
  border-bottom: 1px solid #4c6085;
  height: 83px;
  width: 100%;
}

.headerbar > .logo {
  display: inline-block;
  color: white;
  margin-left: 20px;
  margin-right: 45px;
  height: 42px;
}

.headerbar > .dropdowns {
  padding: 0px 0px 0px 40px;
}

.bar {
  height: 42px;
}

.right-section {
  position: absolute;
  right: 20px;
  vertical-align: middle;
  line-height: 24px;
}

@media (850px < width <= 1450px) {
  .headerbar {
    height: 120px;
  }

  .headerbar > .dropdowns {
    flex-basis: 100%;
    padding: 0px;
    align-self: center;
    text-align: center;
  }
}

@media (width <= 850px) {
  .bar {
    display: none;
  }

  .headerbar > .logo {
    flex-basis: 100%;
    text-align: center;
  }

  .right-section {
    position: relative;
    flex-basis: 100%;
    text-align: center;
    margin: 20px 0px;
  }

  .headerbar {
    height: auto;
  }

  .headerbar > .dropdowns {
    flex-basis: 100%;
    padding: 0px;
    align-self: center;
    text-align: center;
  }
}
</style>
