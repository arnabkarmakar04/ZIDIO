For Speech Emotion Recognition: 
  Dataset is too large to drop here, if you can download & rename it as it mentioned ('Path\\Speech_data'), it will work perfectly.. 
  Otherwise you can simply download it from kaggle from the following code:

Cell 1:
!pip install kaggle
!mkdir ~/.kaggle
!cp kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json
!kaggle datasets download ejlok1/toronto-emotional-speech-set-tess
zip_filename = 'toronto-emotional-speech-set-tess.zip' 
!unzip -o {zip_filename} -d ./TESS
from pathlib import Path
import os
import pandas as pd

Cell 2:
dataset_dir = Path('./TESS/Toronto Emotional Speech Set Data') 
audio_paths = list(dataset_dir.glob('**/*.wav'))
emotion_labels = [os.path.split(os.path.split(path)[0])[1] for path in audio_paths]
audio_df = pd.DataFrame({'audio_file': audio_paths, 'emotion': emotion_labels}).sample(frac=1).reset_index(drop=True)

Rest of the codes....
