<template>
  <div class="timeline" v-if="timelineData.length > 0">
    <ul class="timeline-list">
      <template v-for="item in timelineData">
        <li class="timeline-item" :key="item.id">
          <div class="timeline-item-content">
            <b class="timeline-item-date">{{ getDate(item.date) }}</b>
            <p class="timeline-item-desc">{{ item.desc }}</p>
          </div>
        </li>
      </template>
    </ul>
  </div>
</template>

<script>
import moment from "moment";
export default {
  name: "TimeLine",
  props: {
    timelineData: {
      type: Array,
      required: true,
    },
  },
  methods: {
    getDate(date) {
      return moment(date).fromNow();
    },
  },
};
</script>

<style lang="scss" scoped>
.timeline {
  position: relative;
  padding: 20px;
  
  &:before {
    content: "";
    position: absolute;
    height: 100%;
    width: 3px;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: #3e3e3e;
  }

  &-list {
    list-style: none;
  }

  &-item {
    padding: 10px;
    background-color: #3e3e3e;
    border-radius: 5px;

    &:before {
      content: "";
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      border-radius: 50%;
      background-color: #3e3e3e;
      height: 20px;
      width: 20px;
      font-size: 11px;
      color: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    &:nth-child(odd) {
      transform: translateX(-60%);
      &:before {
        right: -28px;
      }
    }
    &:nth-child(even) {
      transform: translateX(60%);
      &:before {
        left: -28px;
      }
    }
    &:not(:last-child) {
      margin-bottom: 30px;
    }
    &-date {
      font-size: 14px;
    }
    &-desc {
      font-size: 15px;
    }
  }
}
</style>
