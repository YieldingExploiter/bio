<!-- mute button when :troll: -->
<script lang="ts">
  import baseRoute from '../BaseRoute';

  const sounds = [
    '/music/GenshinOST/The Wind and The Star Traveler/A Day in Mondstadt [muSibQfpHTE].mp3',
    "/music/GenshinOST/The Wind and The Star Traveler/A Storm, A Spire, and A Sanctum (Dvalin's Nest) [d1q9ahJCpLc].mp3",
    '/music/GenshinOST/The Wind and The Star Traveler/A Sweet Smile [Ql4kh7XFsps].mp3',
    '/music/GenshinOST/The Wind and The Star Traveler/A Tale of Two Dragons [SgvHmGCVZqs].mp3',
    '/music/GenshinOST/The Wind and The Star Traveler/Caelestinum Finale Termini [VqtScyk2C5A].mp3',
    '/music/GenshinOST/The Wind and The Star Traveler/Dawn Winery Theme [wdfgkJwfit8].mp3',
    '/music/GenshinOST/The Wind and The Star Traveler/Genshin Impact Main Theme [EEYMlUVKmyE].mp3',
    '/music/GenshinOST/The Wind and The Star Traveler/Happy Journey [zfdIFm6CDe8].mp3',
    '/music/GenshinOST/The Wind and The Star Traveler/Knighthood Excellence [uZC1F1pAAZM].mp3',
    '/music/GenshinOST/The Wind and The Star Traveler/Lone Sojourner [IaXxCLXbowg].mp3',
    '/music/GenshinOST/The Wind and The Star Traveler/Pure Sky [qHNvq6mBNg4].mp3',
    '/music/GenshinOST/The Wind and The Star Traveler/Rite of Battle [M3CoUlbjQMs].mp3',
    '/music/GenshinOST/The Wind and The Star Traveler/The Edge of the Prairie [udfm0ff2XOg].mp3',
    '/music/GenshinOST/The Wind and The Star Traveler/The Outlander Who Caught the Wind [Asa9D0HwJgA].mp3',
  ].map((v) => `${baseRoute}${v}`);
  const getRandomSound = () =>
    sounds[Math.floor(Math.random() * sounds.length)];
  let sound = sounds[0];
  setInterval(() => {
    const el = document.querySelector('[data-genshin-ost]') as HTMLAudioElement;
    el.volume = 0.1;
  }, 500);
</script>

<audio
  src={sound}
  on:ended={() => {
    sound = getRandomSound();
    // @ts-ignore
    document.querySelector('[data-genshin-ost]').src = sound;
    // @ts-ignore
    document.querySelector('[data-genshin-ost]').play();
  }}
  data-autoplay
  data-genshin-ost
/>
