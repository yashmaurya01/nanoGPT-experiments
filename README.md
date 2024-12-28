# nanoGPT-experiments
Following Andrej Karpathy's tutorial for building nanoGPT from scratch (https://www.youtube.com/watch?v=kCc8FmEb1nY)

## About
This repo contains my experiments with the nanoGPT model explained in the tutorial. The model is only the decoder part of the transformer and trained on mini shakespeare dataset. The video walks throught the explanation of each decision for each line of code and must watch to understand attention in detail.
The training and validation loss went from `train loss 3.6488, val loss 3.6718` initially to `train loss 1.1882, val loss 1.4933` after 2000 epochs.

Note: This code only covers the pretraining of a decoder model, so its still a smart document completer and will keep rambling tokens without stopping, if max_tokens would be set to a high number. The next step would be alignment tuning this model to a more QnA format which the GPT models are known for. RLHF is used to do this; Proximal policy optimization is something which OpenAI used to tune this model and mostly the secret sauce for the amazing GPT results.

## How to run
Just run the main.ipynb file. It will download the dataset, preprocess it and train the model. 

Initially, I was running everything locally on my macbook pro. But the training was too slow and I had to move to google colab. The colab notebook is also in the repo.

The final code took roughly 27 minutes to run on colab on the T4 GPU for 2000 epochs.

## Results
Just with a Bigram model I got this:

```text
UKENTUCA:
A: bere-
Herih cave,
Me p th,
PAThagusorthatheve my LIOxffice sks; thintonges man bims Ne.
HAnt prd ffr itass inilfrthyorss ard themert d athambour'shomese ang o's, decowa ato
Th,
BIILisid.
MPor icechatrevand;
Herert isthe ca e mbus!
COLAn pry owouilld
Thay de wir:
Whind w ilound ty, hethalod l, yer tcratem be argh-
NELLIUCLINIsoce s thatllid aigo thod, atemen schak br, awor he ishee my uig witot h thesin than t sheramof akshee y.
Yo, misucar MPOLesthn tibur, s;
Stist bu IO, ny the murunt nard An y turyrinteruthownshe men te
To chanenessar hisolouscourgofterd, r by.
Andonin ipoumemed f f oumy mior s thitartomaveyot ncor'

We the And alers IENGUngis bthods fe h t IOLakndoouco aly t y, stheabet Wo eisondan we.

MNERUMA id ge bupelacosenmur! angrnde

Yory thathe m ISThe 'd n, fau?
t ave RKI sonsioron:
MAn n

Baisheswicu ar meshaloutsewoutyomatheledenomugs; shit s,
ADUENCormalindie oimmbofoun:
Ford, XE:
he the, llimengash hirsowig agimy sertacous st fame t swarwiowhthe th me ie
```

After adding multiheaded attention, layer normalization, model intializations, MLPs, and residual connections, the model was able to generate more coherent text.

```text
OXFORDANLEY:
Ay, shall I he3 KING HENRY VI:
How now, Northumble should she dear.

DUKE OF YORK:
Senless they a conquer provered with a war,
To with ba prayers fr a joy abhoad himself
And posterity and Glod, instering kingdomy
That did ewith feast word you contented:
All mess a turn this leans almost.
The hour true is in great sworn: you have littled a word,
Win play still as i' the fair abll,
And too harm floces with a disperited of beje
I had womaning all day encounted:
Therefore the shall wealling the king his holy case,
Stand from my mornsal thanks malices,
Though the seople doth good, dost general.

First Servant:
O hath remedy, and loathed was the lack,
Or, these weed from the treasons satoch
Are ne'er feel. Although, seeing hates been prival,
One a dancoured nobour?

MENENIUS:
My brave is answer my heads!
And would yet here's a prated I say; I'll keep
The edge pity for Cominius, and rememberal.

MENIUS:
When it
Was datches; for thick? that's treamily, another neither?

MEssenger
```
