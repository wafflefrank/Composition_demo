<template>
  <header class="header_style pb-3">
    <div class="navbar">
      <div class="d-flex flex-fill align-items-center justify-content-center">
        <img class="home_logo" src="../../assets/Logo/logo_kolapay.jpg" alt="#" />
        <h1 class="text-start">玩具<br />KOLA</h1>
      </div>
      <!-- Navbar右邊選單 -->
      <div class="l-content me-5 mt-3">
        <div class="d-flex align-items-center">
          <div class="moon_style d-flex align-items-center">
            <!-- <i class="fa-solid fa-moon fs-4 ms-3"></i
          > -->
            <el-switch
              class="dark_switch"
              :class="[isDark === true ? 'dark_switch' : 'white_switch']"
              v-model="isDark"
              style="--el-switch-on-color: #f2f2f2; --el-switch-off-color: #2c2c2c"
              @change="toggleMode(isDark)"
            />
          </div>
          <el-dropdown class="ms-3" trigger="click" :hide-on-click="false" size="small">
            <span class="el-dropdown-link">
              <el-icon class="el-icon--right">
                <i class="fa-solid fa-bars fs-2"></i>
                <arrow-down class="arrow"></arrow-down>
              </el-icon>
            </span>

            <template #dropdown>
              <el-dropdown-menu>
                <el-dropdown-item class="hamburger_list">test</el-dropdown-item>
                <el-dropdown-item>登出</el-dropdown-item>
              </el-dropdown-menu>
            </template>
          </el-dropdown>
        </div>
      </div>
    </div>
    <ul class="topBar-menu d-flex align-items-center justify-content-center">
      <li><a href="#bedAdvantage">床墊優勢</a></li>
      <li><a href="#recommendation">好評推薦</a></li>
      <li><a href="#transport">運送方式</a></li>
      <li><a href="#orderInfo">立即預訂</a></li>
    </ul>
  </header>
</template>

<script>
// import sunLogo from '../../assets/Logo/icons8-moon-and-stars-30.png';

export default {
  data() {
    return {
      // 是否擴展
      isExpand: true,
      // dark mode
      isDark: true,
    };
  },
  methods: {
    clickMenu(item) {
      this.$store.commit('selectMenu', item);
    },
    clickExpand() {
      if (this.isExpand === true) {
        this.isExpand = false;
      } else {
        this.isExpand = true;
      }
    },
    // 切換Dark模式
    toggleMode(isDark) {
      console.log(isDark);
      if (this.isDark === false) {
        document.documentElement.setAttribute('data-theme', 'light');
        localStorage.setItem('theme', 'light');
      } else if (this.isDark === true) {
        document.documentElement.setAttribute('data-theme', 'dark');
        localStorage.setItem('theme', 'dark');
      }
    },
  },
  created() {
    const currentTheme = localStorage.getItem('theme') ? localStorage.getItem('theme') : null;
    console.log(currentTheme);
    if (currentTheme) {
      document.documentElement.setAttribute('data-theme', currentTheme);

      if (currentTheme === 'dark') {
        this.isDark = true;
        // toggleSwitch.checked = true;
      } else {
        this.isDark = false;
      }
    }
  },
};
</script>

<style lang="scss" scoped>
// LOGO樣式
.home_logo {
  border-radius: 10px;
  width: 90px;
  margin: 8px 25px 24px 40px;
  background: black;
  // box-shadow: -1px 1px 24px 4px var(--logo-shadow-color);
  // -webkit-box-shadow: -1px 1px 24px 4px var(--logo-shadow-color);
  // -moz-box-shadow: -1px 1px 24px 4px var(--logo-shadow-color);
}
// 玩具KOLA
.text-start {
  color: var(--font-color);
}
.el-button {
  padding: 5px 5px;
}
.header_style {
  // height: 350px !important;
  background: var(--heading-color);
  // align-items: flex-start;
}
.navbar {
  align-items: flex-start;
  // // justify-content: space-between;
  // // height: 160px;
  // background: var(--heading-color);
  // //   margin-left: 30px;
  color: #000;
}
.arrow {
  font-size: 20px;
  color: white;
}
// .l-content {
//   display: flex;
// }

.moon_style {
  :deep(.el-switch__core .el-switch__action) {
    background-image: url('../../assets/Logo/icons8-moon-and-stars-30.png') !important;
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
  }
}

.el-dropdown-link {
  margin-right: 30px;
}
.el-icon--right i {
  color: var(--font-color);
}
.hamburger_style {
  a {
    list-style: none;
    height: 100%;
    background-color: transparent;
    display: flex;
    align-items: center;
    height: 100%;
    width: 100%;
    border-radius: 6px;
    text-decoration: none;
    transition: var(--tran-03);
  }
  &:hover {
    // background: linear-gradient(90deg, rgba(238, 133, 46, 0.19091386554621848) 0%, rgba(252, 241, 69, 0.05926120448179273) 100%);
    & i::before {
      color: #faa30d;
    }
    a {
      color: #faa30d;
      // background-color: var(--text-color);
    }
  }
}
a {
  align-items: center;
  width: 100%;
  color: var(--font-color);
  text-decoration: none;
}
</style>
