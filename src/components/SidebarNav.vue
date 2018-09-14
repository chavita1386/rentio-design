<template>
  <nav class="nav sidebar-nav">
    <div class="profile">
      <img src="../assets/profile.jpg" alt="Name" class="profile__photo">
      <h3 class="profile__name">Adam Smith</h3>
      <p class="profile__info">
        Realtor
        <span class="l-br">-</span> Los Angeles, LA
      </p>
    </div>
    <ul class="menu">
      <li class="menu__item">
        <a href="#" class="menu__link">
          <i class="fas fa-home icon"></i>properties</a>
      </li>
      <li class="menu__item">
        <a href="#" class="menu__link">
          <i class="far fa-map icon"></i>location</a>
      </li>
      <li class="menu__item">
        <a href="#" class="menu__link">
          <i class="far fa-money-bill-alt icon"></i>sales</a>
      </li>
      <li class="menu__item">
        <a href="#" class="menu__link selected">
          <i class="far fa-user icon"></i>clients</a>
      </li>
      <li class="menu__item">
        <a href="#" class="menu__link">
          <i class="far fa-calendar-alt icon"></i>calendar</a>
      </li>
      <li class="menu__item">
        <a href="#" class="menu__link">
          <i class="far fa-comment-alt icon"></i>inbox</a>
      </li>
      <li class="menu__item">
        <a href="#" class="menu__link">
          <i class="far fa-chart-bar icon"></i>stadistics</a>
      </li>
    </ul>
    <div class="logout">
      <a href="#" class="logout__button">
        <i class="fas fa-power-off icon"></i>Log out
      </a>
    </div>
  </nav>
</template>

<script>
export default {

};
</script>
