```sh
# instalar yt-dlp
cd /bin
curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o yt-dlp
chmod a+rx yt-dlp 

#baixar audios
yt-dlp -i --extract-audio --audio-format mp3 --audio-quality 0 --restrict-filenames --output "%(uploader)s%(title)s.%(ext)s" https://www.youtube.com/watch?v=PedrOwqgp9s


#baixar vídeos
yt-dlp --restrict-filenames --output "%(uploader)s%(title)s.%(ext)s" "https://youtu.be/5eN2P83GD-w?si=pua9S8DQSQtHbpG1"
```