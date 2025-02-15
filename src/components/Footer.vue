<template>
  <footer class="footer">
    <div class="container">
      <nav class="nav">
        <ul class="nav-links">
          <li>
            <a href="#"><span>Каталог</span></a>
          </li>
          <li>
            <a href="#"><span>Доставка</span></a>
          </li>
          <li>
            <a href="#"><span>Оплата</span></a>
          </li>
          <li>
            <a href="#"><span>Контакты</span></a>
          </li>
          <li>
            <a href="#"><span>О компании</span></a>
          </li>
        </ul>
      </nav>
      <div class="contact">
        <div class="phone">
          <img src="../assets/img/phone/Vector.png" alt="phone" />
          <h6><a href="tel:+78125555555">+7 (812) 555-55-55</a></h6>
        </div>
        <div class="address">
          <img src="../assets/img/address/Vector.svg" alt="address" />
          <h6>
            <a
              href="https://www.google.com/maps/place/%D0%9F%D0%B0%D1%80%D0%BA%D0%B8%D0%BD%D0%B3+%D1%83%D0%BB.+%D0%95%D1%84%D0%B8%D0%BC%D0%BE%D0%B2%D0%B0+%D0%B4.+3/@59.9252371,30.3196842,19z/data=!4m6!3m5!1s0x469631d345f750a5:0x534b62fe3ea4e93f!8m2!3d59.9253695!4d30.3201067!16s%2Fg%2F11fktdyt1g?authuser=0&entry=ttu&g_ep=EgoyMDI1MDIxMC4wIKXMDSoASAFQAw%3D%3D"
              target="_blank"
              >г. Санкт-Петербург, ул. Ефимова, 3</a
            >
          </h6>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "AppFooter",
};
</script>

<style>
a span {
  font-weight: 400;
  font-size: 14px;
}

.footer {
  max-width: 1920px;
  width: 100%;
  height: auto;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  background-color: #eceaea;
}
.contact {
  display: flex;
  flex-direction: row;
  white-space: nowrap;
  justify-content: space-between;
  width: 100%;
  min-height: 21px;
}
.phone {
  margin-right: 10px;
  display: flex;
  flex-direction: row;
  align-items: center;
  width: 160px;
}
.phone img {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 14px;
  height: 14px;
  object-fit: cover;
  margin-right: 8px;
}

.address {
  display: flex;
  flex-direction: row;
  align-items: center;
  max-width: 285px;
}

.address img {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 14px;
  height: 14px;
  margin-right: 8px;
}

@media (max-width: 480px) {
  .contact {
    flex-direction: column;
    align-items: center;
    margin-bottom: 25px;
  }
  .phone {
    margin: 0 0px 10px 0;
  }
}
</style>
