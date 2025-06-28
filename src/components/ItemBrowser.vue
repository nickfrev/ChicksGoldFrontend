<script setup lang="ts">
import ItemBrowserResults from './ItemBrowserResults.vue'
import SwordIcon from 'vue-material-design-icons/Sword.vue'
import MagnifyIcon from 'vue-material-design-icons/Magnify.vue'
import SackIcon from 'vue-material-design-icons/Sack.vue'
import FeatherIcon from 'vue-material-design-icons/Feather.vue'
import IconDropDown from './IconDropDown.vue'

import { ref } from 'vue'

const items = ref([])
// generate 100 random items
const weaponNames = [
  '/src/assets/images/acceptedPayment.png',
  '/src/assets/images/items/carl-olsen/crossbow.png',
  '/src/assets/images/items/darkzaitzev/flying-shuriken.png',
  '/src/assets/images/items/darkzaitzev/kusarigama.png',
  '/src/assets/images/items/darkzaitzev/north-star-shuriken.png',
  '/src/assets/images/items/darkzaitzev/sharp-shuriken.png',
  '/src/assets/images/items/darkzaitzev/shuriken.png',
  '/src/assets/images/items/darkzaitzev/star-shuriken.png',
  '/src/assets/images/items/darkzaitzev/three-pointed-shuriken.png',
  '/src/assets/images/items/darkzaitzev/whirlpool-shuriken.png',
  '/src/assets/images/items/delapouite/armored-boomerang.png',
  '/src/assets/images/items/delapouite/attack-gauge.png',
  '/src/assets/images/items/delapouite/baseball-bat.png',
  '/src/assets/images/items/delapouite/bo.png',
  '/src/assets/images/items/delapouite/bone-mace.png',
  '/src/assets/images/items/delapouite/boomerang-cross.png',
  '/src/assets/images/items/delapouite/boomerang.png',
  '/src/assets/images/items/delapouite/bow-arrow.png',
  '/src/assets/images/items/delapouite/bow-string.png',
  '/src/assets/images/items/delapouite/brass-knuckles.png',
  '/src/assets/images/items/delapouite/broken-axe.png',
  '/src/assets/images/items/delapouite/claymore-explosive.png',
  '/src/assets/images/items/delapouite/crescent-staff.png',
  '/src/assets/images/items/delapouite/crowbar.png',
  '/src/assets/images/items/delapouite/dagger-rose.png',
  '/src/assets/images/items/delapouite/detonator.png',
  '/src/assets/images/items/delapouite/flail.png',
  '/src/assets/images/items/delapouite/flamethrower-soldier.png',
  '/src/assets/images/items/delapouite/flamethrower.png',
  '/src/assets/images/items/delapouite/flanged-mace.png',
  '/src/assets/images/items/delapouite/gun-rose.png',
  '/src/assets/images/items/delapouite/heavy-bullets.png',
  '/src/assets/images/items/delapouite/hook-swords.png',
  '/src/assets/images/items/delapouite/human-cannonball.png',
  '/src/assets/images/items/delapouite/hunting-bolas.png',
  '/src/assets/images/items/delapouite/laser-turret.png',
  '/src/assets/images/items/delapouite/lasso.png',
  '/src/assets/images/items/delapouite/lead-pipe.png',
  '/src/assets/images/items/delapouite/lunar-wand.png',
  '/src/assets/images/items/delapouite/magic-trident.png',
  '/src/assets/images/items/delapouite/missile-launcher.png',
  '/src/assets/images/items/delapouite/monkey-wrench.png',
  '/src/assets/images/items/delapouite/mortar.png',
  '/src/assets/images/items/delapouite/mp5.png',
  '/src/assets/images/items/delapouite/nunchaku.png',
  '/src/assets/images/items/delapouite/panzerfaust.png',
  '/src/assets/images/items/delapouite/quiver.png',
  '/src/assets/images/items/delapouite/reload-gun-barrel.png',
  '/src/assets/images/items/delapouite/revolver.png',
  '/src/assets/images/items/delapouite/saber-and-pistol.png',
  '/src/assets/images/items/delapouite/sai.png',
  '/src/assets/images/items/delapouite/sawed-off-shotgun.png',
  '/src/assets/images/items/delapouite/sharp-axe.png',
  '/src/assets/images/items/delapouite/silver-bullet.png',
  '/src/assets/images/items/delapouite/skull-staff.png',
  '/src/assets/images/items/delapouite/sling.png',
  '/src/assets/images/items/delapouite/slingshot.png',
  '/src/assets/images/items/delapouite/stake-hammer.png',
  '/src/assets/images/items/delapouite/submarine-missile.png',
  '/src/assets/images/items/delapouite/switch-weapon.png',
  '/src/assets/images/items/delapouite/sword-brandish.png',
  '/src/assets/images/items/delapouite/thor-hammer.png',
  '/src/assets/images/items/delapouite/tomahawk.png',
  '/src/assets/images/items/delapouite/torpedo.png',
  '/src/assets/images/items/delapouite/tribal-gear.png',
  '/src/assets/images/items/delapouite/umbrella-bayonet.png',
  '/src/assets/images/items/delapouite/uzi.png',
  '/src/assets/images/items/delapouite/walking-turret.png',
  '/src/assets/images/items/delapouite/war-axe.png',
  '/src/assets/images/items/delapouite/war-pick.png',
  '/src/assets/images/items/delapouite/warhammer.png',
  '/src/assets/images/items/delapouite/winged-scepter.png',
  '/src/assets/images/items/delapouite/wood-club.png',
  '/src/assets/images/items/delapouite/zat-gun.png',
  '/src/assets/images/items/faithtoken/ninja-star.png',
  '/src/assets/images/items/generalace135/shepherds-crook.png',
  '/src/assets/images/items/john-colburn/pistol-gun.png',
  '/src/assets/images/items/lorc/all-for-one.png',
  '/src/assets/images/items/lorc/andromeda-chain.png',
  '/src/assets/images/items/lorc/archery-target.png',
  '/src/assets/images/items/lorc/arrowhead.png',
  '/src/assets/images/items/lorc/autogun.png',
  '/src/assets/images/items/lorc/axe-in-stump.png',
  '/src/assets/images/items/lorc/backstab.png',
  '/src/assets/images/items/lorc/barbed-spear.png',
  '/src/assets/images/items/lorc/battered-axe.png',
  '/src/assets/images/items/lorc/battle-axe.png',
  '/src/assets/images/items/lorc/beam-wake.png',
  '/src/assets/images/items/lorc/blunderbuss.png',
  '/src/assets/images/items/lorc/bolas.png',
  '/src/assets/images/items/lorc/bolter-gun.png',
  '/src/assets/images/items/lorc/bowman.png',
  '/src/assets/images/items/lorc/broken-bottle.png',
  '/src/assets/images/items/lorc/bullets.png',
  '/src/assets/images/items/lorc/cannon-ball.png',
  '/src/assets/images/items/lorc/cannon-shot.png',
  '/src/assets/images/items/lorc/cannon.png',
  '/src/assets/images/items/lorc/crossed-pistols.png',
  '/src/assets/images/items/lorc/crossed-sabres.png',
  '/src/assets/images/items/lorc/crossed-swords.png',
  '/src/assets/images/items/lorc/crystal-wand.png',
  '/src/assets/images/items/lorc/double-shot.png',
  '/src/assets/images/items/lorc/dripping-knife.png',
  '/src/assets/images/items/lorc/fairy-wand.png',
  '/src/assets/images/items/lorc/flaming-trident.png',
  '/src/assets/images/items/lorc/flash-grenade.png',
  '/src/assets/images/items/lorc/grapple.png',
  '/src/assets/images/items/lorc/grenade.png',
  '/src/assets/images/items/lorc/gunshot.png',
  '/src/assets/images/items/lorc/halberd-shuriken.png',
  '/src/assets/images/items/lorc/harpoon-chain.png',
  '/src/assets/images/items/lorc/harpoon-trident.png',
  '/src/assets/images/items/lorc/heavy-arrow.png',
  '/src/assets/images/items/lorc/high-shot.png',
  '/src/assets/images/items/lorc/laser-blast.png',
  '/src/assets/images/items/lorc/lightning-bow.png',
  '/src/assets/images/items/lorc/mace-head.png',
  '/src/assets/images/items/lorc/machete.png',
  '/src/assets/images/items/lorc/minigun.png',
  '/src/assets/images/items/lorc/missile-pod.png',
  '/src/assets/images/items/lorc/missile-swarm.png',
  '/src/assets/images/items/lorc/pincers.png',
  '/src/assets/images/items/lorc/pocket-bow.png',
  '/src/assets/images/items/lorc/ray-gun.png',
  '/src/assets/images/items/lorc/reticule.png',
  '/src/assets/images/items/lorc/saber-slash.png',
  '/src/assets/images/items/lorc/sabers-choc.png',
  '/src/assets/images/items/lorc/sacrificial-dagger.png',
  '/src/assets/images/items/lorc/scalpel-strike.png',
  '/src/assets/images/items/lorc/scythe.png',
  '/src/assets/images/items/lorc/sentry-gun.png',
  '/src/assets/images/items/lorc/shuriken.png',
  '/src/assets/images/items/lorc/slavery-whip.png',
  '/src/assets/images/items/lorc/sparkling-sabre.png',
  '/src/assets/images/items/lorc/spiked-mace.png',
  '/src/assets/images/items/lorc/spray.png',
  '/src/assets/images/items/lorc/stiletto.png',
  '/src/assets/images/items/lorc/stone-spear.png',
  '/src/assets/images/items/lorc/supersonic-bullet.png',
  '/src/assets/images/items/lorc/sword-clash.png',
  '/src/assets/images/items/lorc/sword-in-stone.png',
  '/src/assets/images/items/lorc/sword-spade.png',
  '/src/assets/images/items/lorc/tesla-turret.png',
  '/src/assets/images/items/lorc/trefoil-shuriken.png',
  '/src/assets/images/items/lorc/trident.png',
  '/src/assets/images/items/lorc/wave-strike.png',
  '/src/assets/images/items/lorc/whip.png',
  '/src/assets/images/items/lorc/winged-sword.png',
  '/src/assets/images/items/lorc/wizard-staff.png',
  '/src/assets/images/items/pierre-leducq/anti-aircraft-gun.png',
  '/src/assets/images/items/quoting/field-gun.png',
  '/src/assets/images/items/sbed/ammo-box.png',
  '/src/assets/images/items/sbed/chaingun.png',
  '/src/assets/images/items/sbed/duel.png',
  '/src/assets/images/items/sbed/grenade.png',
  '/src/assets/images/items/sbed/laser-gun.png',
  '/src/assets/images/items/sbed/rifle.png',
  '/src/assets/images/items/sbed/shotgun.png',
  '/src/assets/images/items/sbed/turret.png',
  '/src/assets/images/items/skoll/baton.png',
  '/src/assets/images/items/skoll/bayonet.png',
  '/src/assets/images/items/skoll/drop-weapon.png',
  '/src/assets/images/items/skoll/famas.png',
  '/src/assets/images/items/skoll/gladius.png',
  '/src/assets/images/items/skoll/lee-enfield.png',
  '/src/assets/images/items/skoll/luger.png',
  '/src/assets/images/items/skoll/nuclear-bomb.png',
  '/src/assets/images/items/skoll/spiked-ball.png',
  '/src/assets/images/items/skoll/spiked-bat.png',
  '/src/assets/images/items/skoll/steyr-aug.png',
  '/src/assets/images/items/skoll/stick-grenade.png',
  '/src/assets/images/items/skoll/tec-9.png',
  '/src/assets/images/items/skoll/telescopic-baton.png',
  '/src/assets/images/items/skoll/teller-mine.png',
  '/src/assets/images/items/willdabeast/orb-wand.png',
]

function getWeaponNameFromImageURL(imageURL) {
  const weaponName = imageURL.split('/').pop()?.split('.')[0].replace('-', ' ') || `Weapon ${i + 1}`

  return weaponName
    .split(' ')
    .map((word) => {
      if (word.length === 0) {
        return '' // Handle empty strings if present
      }
      return word.charAt(0).toUpperCase() + word.slice(1)
    })
    .join(' ')
}

for (let i = 0; i < 208; i++) {
  const weaponImageURL = weaponNames[Math.floor(Math.random() * weaponNames.length)]
  const weaponName = getWeaponNameFromImageURL(weaponImageURL)
  const newItem = {
    id: `item-${i}`,
    isOnSale: Math.random() > 0.5,
    quantity: Math.floor(Math.random() * 5),
    name: weaponName,
    description: `Lorem ipsum dolor sit amet consetetur sadipscing elitr.`,
    price: (Math.random() * 3000).toFixed(2),
    gameLogo: `https://picsum.photos/200/100?random=${i}`,
    imageUrl: weaponImageURL,
  }
  newItem.salePrice = newItem.isOnSale ? (Math.random() * newItem.price).toFixed(2) : undefined
  items.value.push(newItem)
}
</script>

<template>
  <h1>Condimentum consectetur</h1>
  <div class="search-control">
    <div class="search-dropdowns">
      <IconDropDown
        class="game-filter-dropdown glass"
        title="Select a Game"
        :options="[
          { value: 'gmod', label: 'GMod' },
          { value: 'halo', label: 'Halo' },
          { value: 'runescape', label: 'Runescape' },
        ]"
      >
        <template v-slot:icon>
          <SwordIcon class="sword-icon" />
        </template>
      </IconDropDown>
    </div>

    <div class="search-bar glass">
      <div class="magnifying-glass">
        <MagnifyIcon />
      </div>
      <div class="search-input-container">
        <input type="text" placeholder="Search" class="search-input" />
      </div>
    </div>
  </div>

  <div class="search-dropdowns">
    <IconDropDown
      class="side-filter-dropdown glass"
      title="Price"
      :options="[
        { value: 'all', label: 'All', default: true },
        { value: 'cheap', label: 'Cheapo' },
        { value: 'expensive', label: 'Expensivo' },
      ]"
    >
      <template v-slot:icon>
        <SackIcon class="side-icon" />
      </template>
    </IconDropDown>
    <IconDropDown
      class="side-filter-dropdown glass"
      title="Item Type"
      :options="[
        { value: 'all', label: 'All', default: true },
        { value: 'weapon', label: 'Weapon' },
        { value: 'armor', label: 'Armor' },
      ]"
    >
      <template v-slot:icon>
        <FeatherIcon class="side-icon" />
      </template>
    </IconDropDown>
  </div>
  <ItemBrowserResults :showAmount="20" :items="items" />
</template>

<style scoped>
h1 {
  font-size: 2.5rem;
}

.search-control {
  margin: 15px 0 20px 0;
  display: flex;
}

.sword-icon {
  color: white;
}

.side-icon {
  color: #39e29d;
}

.glass {
  background-color: rgba(73, 91, 126, 0.2);
}

.search-dropdowns {
  display: inline-block;
}

.game-filter-dropdown {
  border-radius: 5px;
  width: 300px;
}

.search-bar {
  display: inline-block;
  position: relative;
  width: 300px;
  height: 50px;
  border-radius: 5px;
  margin-left: 10px;
  line-height: 50px;
}

.magnifying-glass {
  display: inline-block;
  position: absolute;
  left: 0px;
  top: 0px;
  bottom: 0px;
  width: 50px;
  height: 50px;

  padding-top: 8px;
  padding-left: 20px;
}

.search-input-container {
  display: inline-block;
  position: absolute;
  left: 50px;
  right: 0px;
  top: 0px;
  bottom: 0px;
  height: 50px;
}

.search-input-container input {
  width: 100%;
  height: 100%;
  background-color: transparent;
  border: none;
  color: white;
  font-size: 1rem;
}

::placeholder {
  color: rgb(187, 187, 187);
  font-size: 0.9rem;
  opacity: 1; /* Firefox */
}
</style>
