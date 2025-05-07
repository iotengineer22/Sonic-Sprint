## Test Audio-Data

This audio data was used for testing purposes.
The audio was generated using the Google Cloud Text-to-Speech service, based on the introductory text of the nRF5340 documentation.

Separate audio tracks were created for English, German, Chinese, and Spanish.
https://cloud.google.com/text-to-speech

https://www.nordicsemi.com/Products/nRF5340



These individual language tracks were then mixed or combined using ffmpeg into either 2-channel (2-language) or 4-channel (4-language) audio files.
Examples of the ffmpeg commands used for both 2-channel and 4-channel mixing are provided.

2ch

ffmpeg -i nRF5340_en.wav -i nRF5340_ge.wav -filter_complex "[0:a]pan=mono|c0=c0[left];[1:a]pan=mono|c0=c0[right];[left][right]amerge=inputs=2[a]" -map "[a]" nRF5340_en_ge.wav

4ch

ffmpeg -i nRF5340_en.wav -i nRF5340_ge.wav -i nRF5340_cn.wav -i nRF5340_sp.wav -filter_complex "[0:a][1:a][2:a][3:a]amerge=inputs=4[a]" -map "[a]" nRF5340_4ch_en_ge_cn_sp.wav
