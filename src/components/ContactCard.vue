<script>
export default {
  props: {
    contact: {
      type: Object,
      required: true,
    },
  },
};
</script>

<template>
  <div>
    <div class="p-1">
      <strong>Tên:</strong>
      {{ contact.name }}
    </div>

    <div class="p-1">
      <strong>E-mail:</strong>
      {{ contact.email }}
    </div>

    <div class="p-1">
      <strong>Địa chỉ:</strong>
      {{ contact.address }}
    </div>

    <div class="p-1">
      <strong>Điện thoại:</strong>
      {{ contact.phone }}
    </div>

    <div class="p-1">
      <strong>Liên hệ yêu thích:</strong>

      <div class="mt-2">

        <span
          v-if="contact.favoriteFamily"
          class="badge badge-danger mr-2"
        >
          <i class="fas fa-home"></i>
          Gia đình
        </span>

        <span
          v-if="contact.favoriteFriend"
          class="badge badge-success mr-2"
        >
          <i class="fas fa-user-friends"></i>
          Bạn bè
        </span>

        <span
          v-if="contact.favoriteWork"
          class="badge badge-primary mr-2"
        >
          <i class="fas fa-briefcase"></i>
          Công việc
        </span>

        <span
          v-if="
            !contact.favoriteFamily &&
            !contact.favoriteFriend &&
            !contact.favoriteWork
          "
          class="text-muted"
        >
          Không thuộc nhóm nào
        </span>

      </div>
    </div>
  </div>
</template>