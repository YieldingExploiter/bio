<!-- mute button when :troll: -->
<script lang="ts">
  import baseRoute from '../BaseRoute';

  const sounds = [
    '/music/GenshinOST/A Day in Mondstadt [muSibQfpHTE].mp3',
    '/music/GenshinOST/A Storm, A Spire, and A Sanctum (Dvalin\'s Nest) [d1q9ahJCpLc].mp3',
    '/music/GenshinOST/A Sweet Smile [Ql4kh7XFsps].mp3',
    '/music/GenshinOST/A Tale of Two Dragons [SgvHmGCVZqs].mp3',
    '/music/GenshinOST/Caelestinum Finale Termini [VqtScyk2C5A].mp3',
    '/music/GenshinOST/Dawn Winery Theme [wdfgkJwfit8].mp3',
    '/music/GenshinOST/Genshin Impact Main Theme [EEYMlUVKmyE].mp3',
    '/music/GenshinOST/Happy Journey [zfdIFm6CDe8].mp3',
    '/music/GenshinOST/Knighthood Excellence [uZC1F1pAAZM].mp3',
    '/music/GenshinOST/Lone Sojourner [IaXxCLXbowg].mp3',
    '/music/GenshinOST/Pure Sky [qHNvq6mBNg4].mp3',
    '/music/GenshinOST/Rite of Battle [M3CoUlbjQMs].mp3',
    '/music/GenshinOST/The Edge of the Prairie [udfm0ff2XOg].mp3',
    '/music/GenshinOST/The Outlander Who Caught the Wind [Asa9D0HwJgA].mp3',
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
