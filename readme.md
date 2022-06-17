Environment
-----------

* h5py==2.10.0
* Keras==2.0.8
* numpy==1.19.5
* profilehooks==1.12.0
* pyperclip==1.8.2
* python-chess==0.25.1
* QtPy==1.11.3
* scipy==1.7.3
* stockfish==3.18.0
* tensorboard==1.15.0
* tensorflow-gpu==1.15.2


Quick Start
-------

### Installlation

Enter the root directory of this repo.

```bash
pip install -r requirements.txt
```


### Supervised Learning Data

For supervied learning, you need to make sure there are some game recording files in `data/play_data` (like PGN file).

Run the command at the root of repo.

```bash
python src/chess_zero/run.py --cmd sl 
```

The program will automatically transform the game records into `json` file which we need for model training.
you can download big PGN files (chess files) and paste them into the `data/play_data` folder ([FICS](http://ficsgames.org/download.html) is a good source of data). You can also use the [SCID program](http://scid.sourceforge.net/) to filter by headers like player ELO, game result and more.

**To avoid overfitting, I recommend using data sets of at least 3000 games and running at most 3-4 epochs.**


### Reinforcement Learning

```bash
python src/chess_zero/run.py --cmd self 
```

It will automatically output game data in `data/play_data`.

### Training and Evaluation

Make sure there are no old model in  `data/model/next_generation` before starting training

```bash
python src/chess_zero/run.py --cmd opt 
python src/chess_zero/run.py --cmd eval 
```

Evaluation will compare the performance of model in `data/model/next_generation` and the previous best model in `data/model`.

### Options

You can select some parameters to adjust the training.

* `--type mini` (default)
* `--type normal`
* `--type distributed`

Which determinate the config of training environment. You can see the detail information in file `src\chess_zero\configs`.

For comparing the Stock fish, the application can be downloaded at ([here]https://stockfishchess.org/download/)


