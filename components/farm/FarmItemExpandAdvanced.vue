<template lang="pug">
.farm-item-expand-advanced
  IncentiveItem(
    v-for="incentive in farm.incentives"
    :incentive="incentive"
    :poolFee="farm.fee"
    :finished="finished"
    @stakeAll="$emit('stakeAll', incentive)"
    @claimAll="$emit('claimAll', incentive)"
    @unstakeAll="$emit('unstakeAll', incentive)"
  )
    template(#actions="{ stat }")
      FarmsTableActions(:row="stat" :staked="stat.staked" :finished="finished" @stake="$emit('stake', stat)" @claim="$emit('claim', stat)" @unstake="$emit('unstake', stat)")
  // TODO Make it separete computed to make it reactive
  // FIXME: MAY BE WE DO NOT NEED IT HERE
  //.incentive-item(v-for="incentive in userStakes")
</template>

<script>
import FarmsTableActions from '~/components/farm/FarmsTableActions'
import IncentiveItem from '~/components/farm/IncentiveItem.vue'
export default {
  name: 'FarmItemExpandAdvanced',

  components: {
    FarmsTableActions,
    IncentiveItem,
  },

  props: ['farm', 'finished'],
}
</script>

<style scoped lang="scss">
.farm-item-expand-advanced {
  display: flex;
  flex-direction: column;
  gap: 8px;
}
</style>
