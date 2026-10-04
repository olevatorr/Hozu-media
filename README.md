# Hozu media

The films on [hozu.org](https://hozu.org), served by GitHub Pages at `https://media.hozu.org/`, so the main
repository does not grow with every new cut.

| File | Used on |
|---|---|
| `video/hozu-site-v1.mp4` | the home page (Watch) |
| `video/hozu-devtools-v2.mp4` | `/devtools` |

## Replacing a film
1. Add it under a new name (`hozu-site-v2.mp4`): browsers and the CDN cache a name for a long time.
2. Point the site at it (`site/features/home/media.ts` in olevatorr/Hozu), with a new poster there.
3. Keep this repository small: rewrite it as one commit holding only the files in use, then force-push.

   ```sh
   git checkout --orphan next && git add -A && git commit -m "Media" && git branch -M next main && git push -f origin main
   ```

Files must be H.264 + AAC MP4 with the `moov` box first (`ffmpeg -movflags +faststart`), so playback starts
before the download ends.
