# MachineLearning-Printer3D-Failer

Desenvolver um modelo de reconhecimento de objetos que opera continuamente em uma impressora 3D, analisando as imagens capturadas por uma câmera para identificar a formação de "spaghetti".

Objetivos específicos
Analisar e pré-processar o conjunto de dados disponível, garantindo a limpeza, normalização e tratamento adequado das variáveis relevantes para a construção do modelo preditivo.
Explorar e avaliar diferentes algoritmos e técnicas de aprendizado de máquina, como transfer learning e redes neurais convolucionais, para identificar o modelo que oferece a melhor precisão na identificação de spaghetti.

Para o modelo yolov8

Passo 1 - Instalação

!pip install pytube
!pip install roboflow
!pip install ultralytics
from roboflow import Roboflow
from ultralytics import YOLO
from PIL import Image
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.patches import Rectangle
import torch
import os
import pandas as pd

Passo 2 - Baixar Dataset do Roboflow

rf = Roboflow(api_key="rvUKE42pZxMtA2T76aCW")
project = rf.workspace("3d-printing-failure").project("spaghetti-3d")
version = project.version(1)
dataset = version.download(“yolov8")

Passo 3 - Para modelo yolov8
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


Para o modelo yolov8andCnn

Passo 1 - Instalação

!pip install pytube
!pip install roboflow
!pip install ultralytics
from roboflow import Roboflow
from ultralytics import YOLO
from PIL import Image
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.patches import Rectangle
import torch
import os
import pandas as pd

Passo 2 - Baixar Dataset do Roboflow
rf = Roboflow(api_key="rvUKE42pZxMtA2T76aCW")
project = rf.workspace("3d-printing-failure").project("spaghetti-3d")
version = project.version(1)
dataset = version.download(“yolov8")

Passo 3 - Alteraçao do arquivo yaml

Esperar baixar o dataset e alterar a pasta do arquivo:
no arquivo '/content/Spaghetti-3D-1/data.yaml'
alterar texto para:

names:
- ['spaghetti','stringing']
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

Passo 4 - Alteração do caminho da variavél model:
Na parte de treino que tiver a variavel model = YOLO("/content/runs/detect/train3/weights/best.pt"), alterar a variavel
model = YOLO("/content/runs/detect/{ALTERAR O TRAIN}/weights/best.pt")
para o ultimo treino executado, que estará em runs, detect, train, estará train1, train2, etc, colocar o último 


Para modelo Faster RCNN
Passo 1 - Instalação
!pip install roboflow
from roboflow import Roboflow

import torch
import torchvision
import pandas as pd
import os
import numpy as np
from PIL import Image
import matplotlib.pyplot as plt
import json
from torchvision.transforms import functional as F
import cv2

Passo 2 - baixar Dataset Roboflow
Baixar dataset
rf = Roboflow(api_key="rvUKE42pZxMtA2T76aCW")
project = rf.workspace("3d-printing-failure").project("spaghetti-3d")
version = project.version(1)
dataset = version.download("coco")
