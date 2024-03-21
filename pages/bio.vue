<template>
  <div class="bio-container">
    <Navbar />

    <div class="content">
      <div class="bio-text-container">
        <div class="bio-title">
          <h1>Bio</h1>
        </div>
        <div class="spacer"></div>
        <div class="bio-content">
          <p>Grip face es el alter ego del artista visual David Oliver.</p>

          <p>Cara de lija - o como le llamaban sus compañeros de patín en la Palma de principios de los 2000- emprende
            su educación estética y visual como una significativa parte de la generación de artistas <i>millenial</i>: a
            base
            de patinar en la calle, leer cómics, ver <i>anime</i>, escuchar música anglosajona y estudiar minuciosamente
            portadas de libros, discos y fanzines. Bajo el auspicio de las corrientes <i>underground</i> americanas de
            los 90, el grafismo utilizado por el punk en los 80 y el arte asiático naif, Grip Face se zambulle en el
            rito iniciático de la plástica del graffitti así como en su posterior deconstrucción; la propia insurrección
            del medio le permite entender - desde una edad bien temprana- el arte como método para la supervivencia. El
            dibujo y la pintura se convierten en armas de destrucción masiva contra la ansiedad del mundo contemporáneo.
            Así da comienzo una multifacética carrera artística que se fundamentará principalmente en reexaminar de
            forma constante la mirada hacia su pléyade.</p>
          <p>Con la vocación del artista-ingeniero, Grip Face tiende puentes entre contextos, elementos, técnicas,
            espacios y personas. Extrae parte de su lenguaje primigenio, cimentado principalmente en el espacio público
            y del cual son representativos los proyectos <i>Doors without destination</i> y <i>Black faces</i>
            (publicado en 2016 en formato de libro homónimo) y lo traslada al espacio privado de las galerías de arte
            contemporáneo mediante instalaciones <i>site-specific</i>, esculturas, pinturas o tapices. Proyectos como
            <i>Not rented to humans</i> o <i>Black rubbish is the future</i> reflectan el desasosiego y malestar
            producidos por ser a la par actores y testigos de la autodestrucción de nuestro hogar. Sus libretas de
            dibujo, que le acompañan desde adolescente - y que constituyen el lado más puro a la vez que oscuro de su
            trabajo- son el preludio de la mayoría de sus piezas acabadas.
          </p>
          <p>Moverse con holgura entre los recovecos parece una cualidad idiosincrática de este artista visual; quizás
            sea porque siempre se vio como un outsider, sin terminar de estar cómodo con ninguna etiqueta y sintiéndose
            a partes iguales ansioso y expectante ante la perspectiva de una sociedad permanentemente enmascarada, que
            parece irremediablemente abocada a la masificación tecnológica, la comunicación a través de dispositivos,
            las relaciones superficiales y la ocultación de lo verdadero.</p>
          <p>De la misma forma en la que una pantalla nos devuelve escalonadamente un mensaje de error en ventanas
            quintuplicadas y superpuestas, la pintura de Grip Face nos brinda un espacio lúdico y lleno de estratos
            donde diseccionar las inquietudes de una generación impaciente, ávida de información -sea o no determinante
            su veracidad- y para la cual el paisaje de Internet es el aparentemente mejor escenario para el correcto
            aprendizaje del <i>savoir faire</i>. Sus telas no entienden de índices impacientes aporreando el lado
            izquierdo del
            ratón; cada capa de información se trabaja de forma precisa y minuciosa, y la técnica no es nunca baladí.
            Cada capa es intervenida, tachada o tapada, configurando así un universo meta, plagado de referencias
            estéticas inherentes a la generación Y (y también a la Z, y seguramente a todas las letras que las sigan) y
            ejecutado con una precisión técnica propia del que aprendió a pintar bajo el yugo de la inmediatez. Éstas
            pertenecen a una serie infinita, una exploración evolutiva que forma parte del proceso de aprendizaje del
            mismo autor que las elabora. Lo que tiene sentido para Grip Face es la continuidad, no ser capaz de ver el
            final, la incertidumbre de hacia donde le llevará la pintura. Vivir la expresión artística como vivimos en
            el mundo, transitoriamente y en un presente incierto.</p>
        </div>
      </div>
    </div>
    <div class="bio-images">
      <!-- Imágenes placeholder, reemplaza las URLs según sea necesario -->
      <img src="/img/portrait.webp" alt="Placeholder Image">
    </div>

    <section>
      <div v-for="(exhib, index) in exhibs" :key="index" class="exhib-container"
        :style="{ backgroundImage: 'url(' + exhib.imageUrl + ')' }">
        <div class="exhib-text-container">
          <div class="exhib-title">{{ exhib.title }}</div>
          <div class="exhib-data">
            <div class="exhib-authors">
              <p>{{ exhib.authors }}</p>
            </div>
            <div class="exhib-dates">
              <p> {{ exhib.dates }}</p>
            </div>
            <div class="exhib-address">
              <p> {{ exhib.address }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <footer class="footer">
      <p>&copy; 2024 Gripface. Todos los derechos reservados.</p>
    </footer>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue';
import '@/assets/css/bios.css';

export default {
  components: {
    Navbar,
  },
  data() {
    return {

      exhibs: [
        {
          title: 'MEMORANDUM OF THE EVERYDAY',
          authors: 'MijuLee, Gripface',
          dates: '23/09/2023-15-11-2023',
          address: 'Carrer de la Misericòrdia 2, Palma de Mallorca',
          imageUrl: '/img/ex01.webp',
        },
        {
          title: 'FIND AN OFFLINE SHELTER',
          authors: 'Gripface, Mijulee',
          dates: '15/05/2023-20/05/23',
          address: 'Rue Froissart, 7 Le Marais, Paris',
          imageUrl: '/img/ex02.webp',

        },
        {
          title: 'COLLECTIVE EXHIBITION',
          authors: 'Ela Fidalgo, Gripface, Marria Pratts, Miju Lee, Michael Staniak',
          dates: '21/04/2023-01-06-2023',
          address: 'Carrer del Molí del Compte 47A, Palma de Mallorca',
          imageUrl: '/img/ex03.webp',

        }
      ]
    }
  }
}
</script>
