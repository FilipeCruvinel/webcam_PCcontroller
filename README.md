# webcam_PCcontroller

# English
## Project proposal
This project aimed to develop an application, using artificial intelligence, capable of changing some computer settings with the webcam -- specifically, sound output volume and monitor brightness.

## Development
### Tools
- Language
    - Python -- Jupyter Notebook
- Libraries
    - openCV
    - MediaPipe -- Holistic
    - Numpy
    - TensorFlow -- LDSM, Dense
    - PyCaw -- AudioUtilities, IAudioEndpointVolume
    - screen_brightness_control

### Gesture recognition
- Definition of 4 gestures, plus 1 control gesture (nothing) -- vol-up increases volume, vol-down decreases volume, bright-up increases brightness, bright-down decreases brightness.
- Dataset:
 - 30 videos for each category, 150 videos in total, captured by my webcam; the gestures were performed by myself.
 - Videos stored in their own directory named 'videos'. In the case of this repository, there is only one video for each gesture in this directory, in order to illustrate them.
- For each video, 30 uniformly distributed frames were considered. In each frame, the MediaPipe Holistic model was applied; and the data of the 30 frames were saved as numpy arrays in the 'gesture-info' directory, in its respective location.
- Neural network
 - 3 LSTM layers;
 - 3 Dense layers;
 - Input structure: numpy structure with 30 arrays with 250 positions each containing the data of the 30 frames.
 - Output structure: array with 5 positions – 4 gestures and "nothing" –, each containing a value from 0 to 1 (probability)

### Changing volume and brightness
- To control the audio, the PyCaw library was used; and, to control screen brightness, was used the screen_brightness_control library.
- If "vol-up" is detected and the volume is less than 100, the audio volume is increased by 10 units or up to the maximum; in the case of "vol-down", if greater than 0, the volume is reduced by 10 units or down to the minimum. If "bright-up" is detected and the brightness is less than 100, the screen brightness is increased by 5 units or up to maximum; In the case of "bright-down", if greater than 0, the brightness is reduced by 5 units or down to the the minimum.

### Real-time detection
- Frames are captured by webcam.
- in 1 for every 2 frames, the MediaPipe Holistic model is applied; and the information is accumulated in a array.
- Once accumulated information from 30 frames, detection is carried out; and, depending on the detected gesture, the volume or brightness is changed or nothing is done.

# Português
## Proposta do projeto
Visou-se, neste projeto, o desenvolvimento de uma aplicação, usando-se de inteligência artificial, capaz de alterar algumas configurações do computador com a webcam -- em específico, volume na saída de som e brilho do monitor.

## Desenvolvimento
### Ferramentas
- Linguagem
    - Python -- Jupyter Notebook
- Bibliotecas
    - openCV
    - MediaPipe -- Holistic
    - Numpy
    - TensorFlow -- LSTM, Dense
    - PyCaw -- AudioUtilities, IAudioEndpointVolume
    - screen_brightness_control

### Reconhecimento de gestos
- Definição de 4 gestos, mais 1 gesto de controle (nothing) -- vol-up aumenta o volume, vol-down diminui o volume, bright-up aumenta o brilho, bright-down diminui o brilho.
- Base de dados:
    - 30 videos para cada categoria, 150 vídeos no total, capturados por minha webcam; os gestos foram realizados por mim mesmo.
    - Vídeos armazenados em diretório próprio com nome 'videos'. No caso deste repositório, encontam-se, nesse diretório, apenas um vídeo para cada gesto, afim de ilustrá-los.
- Para cada vídeos foram considerados 30 frames uniformemente distribuídos. Em cada frame, foi aplicado o modelo Holistic do MediaPipe; e os dados dos 30 frames foram salvos como numpy arrays no diretório 'gesture-info', em seu respetivo local.
- Rede neural
    - 3 camadas LSTM;
    - 3 camadas Dense;
    - Estrutura de entrada: estrutura numpy com 30 vetores de 250 posições contendo os dados dos 30 frames.
    - Estrutuda de saída: vetor de 5 posições – 4 gestos e 'nothing' –, cada qual contendo um valor de 0 a 1 (probabilidade)

### Alteração de volume e brilho
- Para controle do audio, foi utilizada a biblioteca PyCaw; e, para contole do brilho na tela, a biblioteca screen_brightness_control.
- Caso seja detectado "vol-up" e o volume seja menor que 100, aumenta-se o volume do audio em 10 unidades ou até o máximo; no caso de "vol-down", diminui-se, se maior que 0, o volume em 10 unidades ou até o mínimo. Caso seja detectado "bright-up" e o brilho seja menor que 100, aumenta-se o brilho da tela em 5 unidades ou até o máximo; no scaso de "bright-down", diminui-se, se maior que 0, o brilho em 5 unidades ou até o mínimo.

### Detecção em tempo real
- Realiza-se a captura das imagens pela webcam.
- A cada 2 frames corridos, em 1 é aplicado o modelo Holistic do MediaPipe; e as informações são acumuladas em um vetor.
- Acumuladas as informações de 30 frames, realiza-se a detecção; e ,dependendo do gesto detectado, executa-se a alteração no volume ou brilho ou não se faz nada.
    

