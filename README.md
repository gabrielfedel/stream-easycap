# Streaming à partir do Linux

# Recursos

* placa easycap (somagic easycap)
* servidor iceacast
* camera com saída rca
* debian ( >= 7 )

# Referências

* https://github.com/stevelacy/EasyCap
    * Driver para linux (com o firmware proprietário)

# pacotes necessários

* oggfwd
* libav-tools

# Comando para visualização com mplayer

sudo somagic-capture -n | mplayer -vf yadif,screenshot -demuxer rawvideo
-rawvideo "ntsc:format=uyvy:fps=30000/1001" -aspect 4:3 -

# Comando para transmissão em ogg e armazenamento de bruto em ogg (só vídeo,
NTSC ):

sudo somagic-capture -n | avconv -f rawvideo -pix_fmt uyvy422 -r 30000/1001 -s
\ ntsc -i - -f ogg - | tee arquivo.ogg | oggfwd -p -n "My RaspberryPi Stream" icecast.server 8000
\ password /mountpoint

# Próximos passos

* Testar áudio
    * à partir da easycap
    * à partir da entrada de áudio

* Testar com câmera para verificar atrasos com vídeo e áudio
