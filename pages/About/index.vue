<template>
  <div class="about-page">
    <!-- Главная секция -->


          <header class="header aboutBg">
            <p class="welcome-text">
              <code>Добро пожаловать в автошколу Виктория</code>
            </p>
            <h1 class="hero-title">
              Научитесь водить<br> с
              <span class="confidence">уверенностью</span>
            </h1>
            <!--<p class="description">
              Профессиональные инструктора и гибкий график занятий.<br>
              <a href="" target="_blank" class="register-link">Зарегистрируйтесь</a> сегодня и начните свой путь к безопасному вождению.<br>
            </p>-->
          </header>



    <!-- Секция "О нашей автошколе" -->
    <section class="contact-section">
      <div class="hero-about">
        <div class="about-content">
          <h2 class="hero-title mt-10 text-2xl leading-7 font-semibold">
            {{ title }} <span class="confidence">Viktorija</span>
          </h2>
          <!-- Uncomment if needed -->
          <!-- <p class="pt-4 text-gray-800 border-t border-dashed">
            <code class="bg-yellow-100 text-xl p-1 rounded border">{{ topic }}</code>
          </p> -->
          <p class="about-paragraph mt-3 text-gray-600">
            {{ paragraph }}
          </p>
        </div><br>
        <div class="about-image">
          <img src="@/assets/img/about_default.jpg" alt="About Image">
        </div>
      </div>
    </section>




    <!-- Секция "Учебный процесс" -->

    <section class="learning-process-section">
      <h2 class="about-title mt-10 text-2xl leading-7 font-semibold">Учебный процесс</h2>
      <h3 class="text-xl">Программа обучения</h3>
      <p>{{ program }}</p><br>
      <h3 class="text-xl">Наши инструкторы:</h3>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-1 gap-6">
      <instructorsList :instructors="instructors"/>
      </div>

      <br><br>
      <h3 class="text-xl">Процедура сдачи экзаменов</h3>
      <p>{{ examProcedure }}</p>
    </section>

    <!-- Секция "Успехи и отзывы" -->
    <section class="success-reviews-section">
      <h2 class="about-title mt-10 text-2xl leading-7 font-semibold">Наши достижения</h2>

      <div class="success-stories-container">
        <div v-for="successStory in successStories" :key="successStory.id" class="success-story-item">
          <h3>{{ successStory.title }}</h3>
          <p>{{ successStory.content }}</p>
        </div>
      </div>

      <h2>Отзывы учеников</h2>

      <div class="reviews-container">
        <div v-for="review in reviews" :key="review.id" class="review-item">
          <img :src="review.image" alt="Reviewer Image" class="review-image" />
          <div class="review-content">
            <p class="review-name">{{ review.name }}</p>
            <p class="review-text">{{ review.text }}</p>
          </div>
        </div>
      </div>

      <!--<div v-for="review in reviews" :key="review.id">
        <p>{{ review }}</p>
      </div>-->
    </section>

    <!-- Секция "Сертификаты и лицензии"
    <section class="certificates-licenses-section">
      <h2>Сертификаты и лицензии</h2>
      <div v-for="certificate in certificates" :key="certificate.id">
        <p>{{ certificate }}</p>
      </div>
      <h2>Партнеры и спонсоры</h2>
      <div v-for="partner in partners" :key="partner.id">
        <p>{{ partner }}</p>
      </div>
    </section>-->

    <!-- Секция "Контакты"
    <section class="contact-section">
      <h2 class="about-title mt-10 text-2xl leading-7 font-semibold">Контактная информация</h2>
      <p>{{ contactInfo }}</p>
      <h2>Карта проезда</h2>
      <div id="map"></div>
      <h2>Мы в социальных сетях</h2>
      <div class="social-media">
        <a v-for="social in socialMedia" :key="social.platform" :href="social.link">{{ social.platform }}</a>
      </div>
    </section> -->
  </div>
</template>



<script>
import instructorsList from '~/components/Instructors/InstructorsList.vue';
import aboutHero from '~/components/aboutHero.vue';
import aboutUs from '~/components/AboutUs.vue';


export default {
  components: { instructorsList, aboutHero, aboutUs,  },
  data() {
    return {
      instructors: [
          { id: 1, name: 'Igor Nagorskii', bio: '', image: require('@/assets/img/instructors/instructor_1.jpg') },
          { id: 2, name: 'Maksim Fedorenko', bio: '', image: require('@/assets/img/instructors/instructor_2.jpg')  },
          { id: 1, name: 'Ivan Skorobogatov', bio: '', image: require('@/assets/img/instructors/instructor_4.jpg')  },
          { id: 2, name: 'Stanislav Zigadlo', bio: '', image: require('@/assets/img/instructors/instructor_3.jpg')  },
          { id: 1, name: 'Andrei Naan', bio: '', image: require('@/assets/img/promo_1.png')  },

        ],
      title: "О нашей автошколе",
      topic: "Ведущая автошкола в Таллине с 18-летним опытом работы",
      paragraph: "Мы гордимся высоким уровнем обучения, который обеспечивается опытными и квалифицированными инструкторами. Наша автошкола предлагает современные методы обучения, включая теоретические занятия и практическое вождение, чтобы подготовить студентов к безопасному и уверенному управлению автомобилем. Присоединяйтесь к нам и получите водительские права!",

      history: 'Краткая история автошколы...',
      mission: 'Миссия и ценности...',
      program: 'Учебный процесс и программа обучения в нашей автошколе включают теоретические и практические занятия. Теория охватывает все аспекты правил дорожного движения и безопасного вождения, а практическая часть включает индивидуальные уроки с опытными инструкторами на современных автомобилях или мотоциклах. Программа обучения ориентирована на основные навыки управления, безопасное вождение и подготовку к экзаменам. Мы предлагаем гибкий график, персонализированный подход и всестороннюю поддержку на каждом этапе обучения.',
      advantages: [
        'Преимущество 1',
        'Преимущество 2'
      ],
      examProcedure: 'Процедура сдачи экзаменов включает два основных этапа: теоретический и практический. На теоретическом экзамене проверяются знания правил дорожного движения и основ безопасности. Практический экзамен оценивает ваши навыки управления автомобилем или мотоциклом в реальных дорожных условиях. Мы предоставляем поддержку и консультации на каждом этапе подготовки, чтобы вы уверенно сдали экзамены и получили водительское удостоверение.',
      achievements: 'Наши достижения...',
      successStories: [
        { id: 1, title: 'История успеха 1 История успеха 1 История успеха 1', content: 'Текст истории... Текст истории... Текст истории... Текст истории... Текст истории... Текст истории... Текст истории... Текст истории...' },
        { id: 2, title: 'История успеха 2 История успеха 2 История успеха 2', content: 'Текст истории... Текст истории... Текст истории... Текст истории... Текст истории... Текст истории... Текст истории...' }
      ],
      reviews: [
        {
          id: 1,
          name: 'Alice Johnson',
          text: 'This is an amazing product! I would definitely recommend it to my friends.',
          image: 'https://via.placeholder.com/60' // Замените на URL изображения
        },
        {
          id: 2,
          name: 'Bob Smith',
          text: 'Not what I expected, but still decent. The quality is acceptable.',
          image: 'https://via.placeholder.com/60' // Замените на URL изображения
        }
        // Добавьте больше отзывов по необходимости
      ],
      certificates: [
        'Сертификат 1',
        'Сертификат 2'
      ],
      partners: [
        'Партнер 1',
        'Партнер 2'
      ],
      contactInfo: 'Контактная информация...',
      socialMedia: [
        { platform: 'Facebook', link: 'https://facebook.com' },
        { platform: 'Instagram', link: 'https://instagram.com' }
      ],
    };
  }
}
</script>

<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Rochester&family=Roboto+Slab:wght@400;700&display=swap');

.success-stories-container {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 20px;
}

.success-story-item {
  background: #f4f9ff; /* Легкий винтажный фон */
  border: 1px solid #d6c8b6; /* Светло-коричневая граница для винтажного эффекта */
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Легкая тень для глубины */
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.success-story-item:hover {
  background-color: #f2e9e0; /* Цвет при наведении */
  transform: scale(1.02); /* Легкое увеличение при наведении */
}

.success-story-item h3 {
  font-family: 'Georgia', serif; /* Винтажный шрифт */
  font-size: 1.5rem;
  font-weight: bold;
  color: #5a4a41; /* Темный коричневый цвет */
  margin-bottom: 10px;
}

.success-story-item p {
  font-family: 'Times New Roman', serif; /* Винтажный шрифт */
  font-size: 1rem;
  color: #6f5e4e; /* Более светлый коричневый цвет */
  line-height: 1.5; /* Межстрочный интервал для лучшей читаемости */
}

.success-story-item::before {
  content: "✦"; /* Декоративный элемент перед заголовком */
  font-size: 2rem;
  color: #c79c6b; /* Золотистый цвет */
  display: block;
  text-align: center;
  margin-bottom: 10px;
}

.reviews-container {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 20px;
}

.review-item {
  display: flex;
  align-items: center;
  background: #ecf2f2; /* Светлый фон, напоминающий старую бумагу */
  border: 1px solid #e0c8a0; /* Легкая граница для винтажного эффекта */
  border-radius: 8px;
  padding: 15px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Легкая тень для глубины */
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.review-item:hover {
  background-color: #f2e4d7; /* Цвет при наведении */
  transform: scale(1.02); /* Увеличение при наведении */
}

.review-image {
  border-radius: 50%;
  width: 60px;
  height: 60px;
  object-fit: cover;
  margin-right: 15px;
}

.review-content {
  display: flex;
  flex-direction: column;
}

.review-name {
  font-family: 'Georgia', serif; /* Винтажный шрифт */
  font-size: 1.1rem;
  font-weight: bold;
  color: #4a3f2e; /* Темно-коричневый цвет */
  margin-bottom: 5px;
}
 
.review-text {
  font-family: 'Times New Roman', serif; /* Винтажный шрифт */
  font-size: 0.95rem;
  color: #6f5e4e; /* Более светлый коричневый цвет */
}

.hero-about {
  display: flex;
  flex-direction: column; /* Stack items vertically */
}

.hero-text {
  flex: 1;
  max-width: 75%;
  text-align: left;
}

.hero-image {
  flex: 1;
  max-width: 25%;
}

.hero-image img {
  width: 100%;
  height: auto;
  border-radius: 12px; /* Округление углов изображения */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2); /* Легкая тень для добавления глубины */
}

.welcome-text {
  font-size: 1.2rem;
  color: #333; /* Темный цвет для контраста */
  margin-bottom: 16px;
}

.hero-title {
  font-size: 2.5rem;
  font-weight: 700; /* Более жирный шрифт для выделения */
  color: #222; /* Темный цвет заголовка */
  margin-bottom: 16px;
}

.confidence {
  color: #007bff; /* Яркий цвет для выделения */
}

.description {
  font-size: 1.1rem;
  color: #555; /* Более светлый цвет для описания */
}

.register-link {
  color: #007bff; /* Цвет ссылки */
  font-weight: 600; /* Жирное начертание ссылки */
  text-decoration: none;
}

.register-link:hover {
  text-decoration: underline; /* Подчеркивание при наведении */
}



.about-page {
  /* background-color: #faf3e0;  Легкий кремовый фон */
  font-family: 'Roboto Slab', serif;
  padding: 2rem;
  border-radius: 10px;
  max-width: 1200px;
  margin: 0 auto;
  /* box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); */
}

section {
  margin-bottom: 40px;
  background-color: #ffffff;
  border: 2px solid #e0ddda;
  border-radius: 10px;
  padding: 20px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  /* transition: transform 0.3s ease, box-shadow 0.3s ease; */
}

/* section:hover {
  transform: scale(1.02);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
} */

h2, h3 {
  font-family: 'Rochester', cursive;
  color: #007bff;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.2);
  margin-bottom: 20px;
}


p, li {
  font-size: 1.2rem;
  color: #333;
}

.social-media a {
  display: inline-block;
  margin-right: 15px;
  color: #3182ce;
  text-decoration: none;
  font-weight: bold;
  text-shadow: 1px 1px 0 #fff;
  transition: color 0.3s ease, transform 0.3s ease;
}

.social-media a:hover {
  color: #007bff;
  transform: scale(1.1);
}

#map {
  height: 300px;
  background: #ccc;
  border: 2px solid #000;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.instructors, .interviews, .success-stories, .reviews, .certificates, .partners, .social-media {
  display: flex;
  flex-wrap: wrap;
}

.instructors > div, .interviews > div, .success-stories > div, .reviews > div, .certificates > div, .partners > div, .social-media > a {
  flex: 1 1 45%;
  margin: 10px;
}

.about-section {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 40px;
}

.contact-section {
  width: 100%;
}


.about-image img {
  width: 100%; /* Ensure image takes full width */
  height: auto; /* Maintain aspect ratio */
}

.about-content, .about-image {
  width: 100%; /* Ensure both sections take full width */
}

.about-title {
  font-size: 2rem;
  font-weight: 600;
  color: #333; /* Цвет заголовка */
  margin-bottom: 16px;
}

.about-paragraph {
  font-size: 1rem;
  font-weight: 100;
  color: #333; /* Цвет заголовка */
  /* margin-top: 16px; */
}

.confidence {
  color: #007bff; /* Яркий цвет для выделения */
}

.pt-4 {
  padding-top: 1rem; /* Отступ сверху */
}

.text-gray-800 {
  color: #333; /* Цвет текста */
}

.border-t {
  border-top-width: 1px;
}

.border-dashed {
  border-style: dashed;
}

.bg-yellow-100 {
  background-color: #faf089; /* Светлый желтый фон */
}

.text-xl {
  font-size: 1.25rem; /* Размер шрифта */
}

.p-1 {
  padding: 0.25rem; /* Отступы */
}

.rounded {
  border-radius: 0.375rem; /* Округление углов */
}

.border {
  border-width: 1px;
}

.mt-3 {
  margin-top: 0.75rem; /* Отступ сверху */
}

.text-gray-600 {
  color: #4a5568; /* Светлый цвет текста */
}

.header {
  padding: 9rem 2rem;
  text-align: center;

  background: #f1f1f1;
  border-bottom: 2px solid #000;
}
.header h1 {
  font-size: 3em;
  margin: 0;
}
.header p {
  margin: 10px 0;
}
.header button {
  padding: 10px 20px;
  background: #4165de;
  color: #fff;
  border: none;
  cursor: pointer;
}
.header a {
  color: #000;
}

.aboutBg {

  background-image: url('@/assets/img/retro-2.jpg'); /* Укажите путь к вашему изображению */
  background-size: cover;
  background-position: center;
}


</style>
