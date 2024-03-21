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
                    Grip face is visual artist David Oliver's alter ego.

                    “Sandpaper head”-thats how his skaterboarding fellows used to call him back in
                    the early 2000s in Palma. Like a significant number of artists belonging to the
                    millennial generation, he initiated his visual and aesthetic education:
                    rollerblading in the streets, reading comics, watching anime, listening to
                    Anglo-Saxon music and thoroughly studying book, cd, and fanzine covers.
                    Under the auspices of the 1990s American underground wave, the graphics
                    used by the Punk movement in the 1980s and the Asian naive art, Grip Face
                    dived into the initiation rite of graffiti plastics as well as in its subsequent
                    deconstruction; very early on, the insurrection of the media itself allowed
                    him to understand art as a means to survive. Drawing and painting turned into
                    weapons of mass destruction against the anxiety of the contemporary
                    world.And thus began a multifaceted artistic career that would revolve mainly
                    around constantly reexamining the very contemplation of his own pleiad.
                    With this vocation to being an artist-engineer, Grip Face bridges the gap
                    between contexts, elements, techniques, spaces and people. He draws part of
                    his primal language, built mainly within the public sphere- represented by
                    projects like Doors without destination and Black faces (published in 2016 in
                    book format under the same title)- shifting it instead to private spaces like
                    galleries of contemporary art through site-specific installations, sculptures,
                    paintings or tapestries.
                    Projects like Not rented to humans or Black rubbish is the future reflect the
                    angst and the distress incurred by being both actors and witnesses of our own
                    home's self-destruction. His sketch books, which he keeps with him since his
                    teens, and which constitute the purest as well as the darkest side of his work,
                    are a prelude to most of his finished works.
                    Moving around with ease among the nooks seems to be an idiosyncratic quality
                    of this visual artist, maybe because he always perceived himself as outsider,
                    never feeling quite comfortable with any tag whatsoever, while feeling equally
                    anxious and always in the expectative when faced with the prospect of a society
                    constantly in disguise. A society that seems irretrievably compelled to
                    technological massification, to communication through devices, to superficial
                    relationships and to the concealment of truth.

                    Similarly to a screen that repeats staggeringly an “error” message in fivefold
                    overlapping windows, Grip Face's painting provides a playful space full of layers
                    within which one may dissect the concerns of an impatient generation, hungry
                    for information- reliable or not- and to whom the internet landscape seems to
                    be the best platform onto which one may learn the savoir-faire properly. His
                    cloths are not familiar with the impatient indexes pommeling on the mouse's
                    left side; every layer of every piece of information is processed in a precise and
                    meticulous way, and the technique is never trivial.

                    Every layer is submitted to intervention, is crossed off or covered, thus shaping
                    a meta universe riddled with aesthetic references that are intrinsic to
                    generation Y (and to generation Z, and, most probably to all future letters to
                    come too for that matter) and implemented with a technical precision of its
                    own, through which he learned to paint under the yoke of immediacy. They all
                    belong to an endless series and an evolving exploration, both part of the
                    author's learning process crafting them. What's meaningful to Grip Face is
                    continuity, this inability to see the end-product, and the uncertainty as to
                    whither the painting will lead it. It's about living the artistic expression the way
                    we live in the world, transiently and in a doubtful present.

                </div>
            </div>
        </div>
        <div class="bio-images">
            <!-- Imágenes placeholder, reemplaza las URLs según sea necesario -->
            <img src="/img/gripfaceesculturaweb.webp" alt="Placeholder Image">
        </div>

        <section>
            <div v-for="(exhib, index) in exhibs" :key="index" class="exhib-container">
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
                    dates: '09/23/2023-11/15/2023',
                    address: 'Carrer de la Misericòrdia 2, Palma de Mallorca',
                },
                {
                    title: 'FIND AN OFFLINE SHELTER',
                    authors: 'Gripface, Mijulee',
                    dates: '05/15/2023-05/20/23',
                    address: 'Rue Froissart, 7 Le Marais, Paris',
                },
                {
                    title: 'COLLECTIVE EXHIBITION',
                    authors: 'Ela Fidalgo, Gripface, Marria Pratts, Miju Lee, Michael Staniak',
                    dates: '04/21/2023-06-01-2023',
                    address: 'Carrer del Molí del Compte 47A, Palma de Mallorca',
                }
            ]
        }
    }
}
</script>
