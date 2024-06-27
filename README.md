# MachineLearning-Printer3D-Failer

Desenvolver um modelo de reconhecimento de objetos que opera continuamente em uma impressora 3D, analisando as imagens capturadas por uma câmera para identificar a formação de "spaghetti".

Objetivos específicos
Analisar e pré-processar o conjunto de dados disponível, garantindo a limpeza, normalização e tratamento adequado das variáveis relevantes para a construção do modelo preditivo.
Explorar e avaliar diferentes algoritmos e técnicas de aprendizado de máquina, como transfer learning e redes neurais convolucionais, para identificar o modelo que oferece a melhor precisão na identificação de spaghetti.



Instalar
!pip install pytube
!pip install roboflow
!pip install ultralytics

Baixar Dataset
rf = Roboflow(api_key="rvUKE42pZxMtA2T76aCW")
project = rf.workspace("3d-printing-failure").project("spaghetti-3d")
version = project.version(1)
dataset = version.download(“yolov8")

Para modelo yolov8
Configuração arquivo
file_path = '/content/Spaghetti-3D-1/data.yaml'

new_content = """
names:
- spaghetti
- stringing
nc: 2
roboflow:
  license: CC BY 4.0
  project: spaghetti-3d
  url: https://universe.roboflow.com/3d-printing-failure/spaghetti-3d/dataset/1
  version: 1
  workspace: 3d-printing-failure
test: /content/Spaghetti-3D-1/test/images
train: /content/Spaghetti-3D-1/train/images
val: /content/Spaghetti-3D-1/valid/images
“""


Para modelo Faster
Baixar dataset
rf = Roboflow(api_key="rvUKE42pZxMtA2T76aCW")
project = rf.workspace("3d-printing-failure").project("spaghetti-3d")
version = project.version(1)
dataset = version.download("coco")
