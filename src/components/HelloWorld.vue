<template>
  <header class="active">
    <div class="container-fluid">
      <div class="logo">
        <a href="#" v-viewer>
          <img src="../assets/img/logo.png" alt="Wooder" />
          <h1 class="hidden">Wooder</h1>
        </a>
      </div>
      <ul class="menu">
        <li><a href="#slider" class="active">HOME</a></li>
        <li><a href="#products">PRODUCTS</a></li>
        <li><a href="#videos">VIDEO</a></li>
        <li><a href="#about">ABOUT</a></li>
        <li><a href="#gallery">GALLERRY</a></li>
        <li><a href="#news">NEWS</a></li>
      </ul>
      <div class="right">
        <div class="lang">
          <div class="lang__current">
            <span>EN</span>
            <i><img src="../assets/img/arrow-language.png" alt=""/></i>
          </div>
          <div class="lang__option">
            <a href="javascript:void(0)">VN</a>
            <a href="javascript:void(0)">JP</a>
            <a href="javascript:void(0)">AU</a>
          </div>
        </div>
        <div class="btnmenu">
          <span></span>
        </div>
      </div>
      <nav class="nav">
        <ul>
          <li><a href="#slider">HOME</a></li>
          <li><a href="#products">PRODUCTS</a></li>
          <li><a href="#videos">VIDEO</a></li>
          <li><a href="#about">ABOUTS</a></li>
          <li><a href="#galllery">GALLERY</a></li>
          <li><a href="#news">NEWS</a></li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script>

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
@import "../components/scss/_variables.scss";
@import "../components/scss/_mixins.scss";
@import "../components/scss/_reset.scss";
@import "../components/scss/_elements.scss";
@import "../components/scss/_components.scss";
@import "../components/scss/_layouts.scss";
// css header
header {
  width: 100%;
  max-width: $container-max-width;
  height: var(--heightHeder);
  position: fixed;
  top: 0;
  left: 0px;
  z-index: 300;
  transition: 0.3s;
  //background: $black-cl;
  &.active {
    background: #000;
    transition: 0.3s;
  }
  .container-fluid {
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;

    .logo {
      img {
        width: 170px;
      }
      .hidden {
        display: none;
      }
    }
    .menu {
      display: flex;
      height: 100%;
      position: absolute;
      left: 50%;
      @include transform(translateX(-50%));
      li {
        a {
          height: 100%;
          display: flex;
          align-items: center;
          justify-content: center;
          font-size: $fz-text;
          line-height: 22px;
          color: #fff;
          opacity: 0.5;
          text-transform: uppercase;
          font-family: pb;
          margin: 0 30px;
          text-decoration: none;
          overflow: hidden;
          @include transition($t);
          position: relative;

          &.active {
            color: $yellow-cl;
          }
          &:after {
            content: "";
            width: 100%;
            height: 2px;
            background-color: #fff;
            position: absolute;
            left: 0;
            bottom: 24px;
            @include transform(scaleX(0));
            @include transform-origin(right center);
            @include transition($t);
          }
          &:hover {
            color: $yellow-cl;
            &:after {
              @include transform(scaleX(1));
              @include transform-origin(left center);
              @include transition($t);
            }
          }
        }
      }
    }
    .right {
      display: inline-flex;
      .lang {
        position: relative;
        height: 100%;
        cursor: pointer;
        &__current {
          display: flex;
          align-items: center;
          height: 100%;
          span {
            font-size: $fz-text;
            line-height: 22px;
            color: #fff;
            opacity: 0.5;
            text-transform: uppercase;
            font-family: pb;
            margin-right: 8px;
          }
          i {
            img {
              width: 10px;
            }
          }
        }
        &__option {
          background-color: #353535;
          position: absolute;
          right: 0;
          top: var(--heightHeder);
          z-index: 198;
          @include visible(0);
          @include transition($t);
          a {
            padding: 7px 20px;
            display: block;
            color: #fff;
            text-transform: uppercase;
            text-decoration: none;
            @include transition($t);
            &:first-child {
              padding-top: 12px;
            }
            &:last-child {
              padding-bottom: 12px;
            }
            &:hover {
              color: $yellow-cl;
              @include transition($t);
            }
          }
        }
        &.active {
          .lang__option {
            @include visible(1);
          }
        }
      }
      .btnmenu {
        display: none;
        width: 40px;
        height: 22px;
        position: relative;
        z-index: 300;
        cursor: pointer;
        margin-left: 20px;
        span {
          width: 100%;
          height: 1px;
          display: block;
          background-color: $yellow-cl;
          position: absolute;
          top: 50%;
          @include transform(translateY(50%));
          @include transition(0.3s);
        }
        &:before,
        &:after {
          content: "";
          width: 100%;
          height: 2px;
          display: block;
          background-color: $yellow-cl;
          @include transition(transform 0.3s);
        }
        &:after {
          position: absolute;
          bottom: 0;
        }
        &.click {
          &:before {
            @include transform(rotate(45deg) translate(6px, 8px));
            @include transition($t);
          }
          span {
            opacity: 0;
            @include transition($t);
          }
          &:after {
            @include transform(rotate(-45deg) translate(4px, -8px));
            @include transition($t);
          }
        }
      }
    }
    .nav {
      display: none;
      &.active {
        opacity: 1;
        pointer-events: auto;
        @include transition(opacity 0.3s);
      }
    }
  }
  @include sm {
    .container-fluid {
      .menu {
        display: none;
      }
      .right {
        .btnmenu {
          display: block;
        }
      }
      .nav {
        display: block;
        width: 100%;
        height: 100vh;
        background-color: $black-cl;
        position: fixed;
        top: 0;
        left: 0;
        @include transform(initial);
        z-index: 100;
        opacity: 0;
        // visibility: hidden;
        // pointer-events: none;
        @include transition(opacity 0.3s);
        ul {
          flex-direction: column;
          @include mid();
          li {
            margin: 0 auto;
            padding: 20px;
            text-align: center;
            a {
              color: $white-cl;
              text-decoration: none;
            }
          }
        }
      }
    }
  }
  @include xs {
    --heightHeader: 60px;
  }
  .btnmenu {
    display: block;
  }
}
</style>
