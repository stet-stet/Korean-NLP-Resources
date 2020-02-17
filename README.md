# Korean-NLP-Resources

지금까지 찾은, 한국어 NLP에 사용 가능한 자원들을 나열해 놓겠습니다.
**다른 자원과 어떻게든 연계해서, 어떻게든 사용해먹을 수 있을 것 같다면 본 리스트에 들어갑니다.**

예. 맞워요. 여기 제 아이디어 노트로 쓰겠단 말이에요. 레포 이름 잘못 정한 것 같습니다.

계속 추가됩니다.

# Corpus (Monolingual)

* [KAIST Corpus](http://semanticweb.kaist.ac.kr/home/index.php/KAIST_Corpus)

70000000 phrase 규모의 말뭉치. 뿐만 아니라 명사 리스트나 명사의 정의, 기술 용어로 가득찬 말뭉치도 배포 중. 누군가가 조국으로 가는 길을 묻거든 고개를 올리라 하지 말고, 시선을 수평으로 유지하여 대전광역시 유성구를 보게 합시다.

* [Universal Dependencies Project](https://universaldependencies.org/)

Treebank를 제공. POS 태깅이랑 비슷하면서도 꽤 다른데, 단순히 "명사"나 "동사"같이 문장에서 하는 역할로 분류를 하는 게 아니라, "이 단어는 저 단어의 목적어" 같이, 단어 사이의 관계를 가지고 태깅을 합니다. 물론, 문장만 써도 됩니다. 446K개 문장. KAIST Treebank가 Kaist Corpus의 일부인지 확인 바람.

* [나무위키 데이터베이스 덤프](https://namu.wiki/w/%EB%82%98%EB%AC%B4%EC%9C%84%ED%82%A4:%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4%20%EB%8D%A4%ED%94%84?from=%EB%82%98%EB%AC%B4%EC%9C%84%ED%82%A4%20%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4%20%EB%8D%A4%ED%94%84)

나무위키에서는 서버에 가하는 부담을 최소화하기 위해 .json 포맷의 데이터베이스 덤프를 제공하며, 압축을 풀면 용량은 10.7GB. 다운받을 때는 1.4GB라는 착한 용량을 자랑합니다.

* [세종 말뭉치](https://ithub.korean.go.kr/user/guide/corpus/guide3.do) 

안 써봤습니다. 양은 꽤 많아보입니다.

# Corpus (Parallel)

한국어 단일언어 말뭉치가 필요하시면, 그냥 Parallel Corpus 받으신 다음에 추출해서 쓰는 것도 좋은 방법입니다. 근데 웹상의 자원을 무슨 마지막 한 톨까지 빨아먹을 특별한 이유가 있는 게 아니면 그냥 그러지 맙시다. 위에 있는 것만으로도 충분하실 것 같은데...

* [TED Corpus](https://github.com/ajinkyakulkarni14/TED-Multilingual-Parallel-Corpus)
Multilingual Parallel Corpus, Bilingual Parallel Corpus. 설명만 보시면 되게 고퀄리티일 것 같지만, 밀려 있거나 불일치하는 부분이 엄청 많이 존재합니다. 이걸 쓰느니 WikiMatrix를 쓸 듯.

* [WikiMatrix](https://github.com/facebookresearch/LASER/tree/master/tasks/WikiMatrix)
특정 언어 페어에 대해선 쓸만한 문장쌍 갯수를 자랑합니다. ja-ko는 ~200k개. 다만 alignment가 완벽하지는 않으니 조심.

* [tatoeba](http://www.manythings.org/anki/)
en-ko 갯수가 빈약하기는 합니다. 언어 따라 다르겠지만, 대략 1k쌍 정도 뽑아낼 수 있다고 생각하시면 됩니다. 일단 겹치는 걸로만 ko-ja 뽑아봤는데 1k개 나옵니다.

* [OPUS](http://opus.nlpl.eu/index.php)
예전엔 어땠는지 모르겠는데, 한국어에 한해서는 문장 갯수도 적고 정확성도 상당히 떨어집니다.

# OCR

* [tesseract](https://github.com/tesseract-ocr/tesseract)
만인의 오픈소스 OCR 도구입니다. 성능은 4.0버젼 이후로 생각보다 나쁘지 않습니다. 다만 흰바탕 검은글씨가 아니면 망합니다. 또, 페이지를 기울일 경우 성능이 저하되는 것으로 의심됩니다. Preprocessing을 정말, 정말, **정말** 잘 해줄 필요가 있습니다.

* [Google Cloud Platform](https://cloud.google.com)
웬만하면 이쪽을 씁시다. 1000장에 1.5 USD. 처음 쓰는 사람한테는 300 USD만큼 크레딧을 무료로 지원해줍니다. 게다가, 문서의 경우 OCR 결과가 위치, 블록 스키 등 여러 정보를 담은 .json 파일로 주어지기 때문에, 페이지의 특정 영역만 골라서 글자를 뽑는 코드를 짜기도 꽤 쉽습니다. Tesseract 쓸 때보다 전처리가 많이 필요하지 않아요. *다만, API의 python wrapper의 경우 documentation이 상당히 빈약하니 조심합니다.*

# Tokenization

* [soynlp](https://github.com/lovit/soynlp) 아직 안 돌려봤습니다. 명사 추출, 단어 추출, 토크나이징, POS 태깅, 벡터화(임베딩같은) 등등, 수많은 기능을 제공합니다. 설명만 봐서는 다른 언어에도 쓰일 수 있을 것 같은데 한 번 확인해보겠습니다.

* [sentencepiece](https://github.com/google/sentencepiece/blob/master/python/README.md)
비지도 학습을 통해서 "형태소"일만한 문자의 조합을 찾아냅니다. 오 엄청 빨리 돌아갑니다.

# Alignment

현재 눈에 쌍심지 켜고 찾아다니는 중입니다. 좋은 방법 아시는 분은 조언 부탁드리겠습니다.

* [STACC 및 그 베리에이션들](http://lrec-conf.org/workshops/lrec2018/W8/pdf/6_W8.pdf) 필요조건: 이미 병렬 말뭉치를 보유하고 있을 것. 그걸 [GIZA++](https://github.com/moses-smt/giza-pp/tree/master/GIZA%2B%2B-v2)에 넣고 돌릴 수 있는 상황일 것. (대소문자 구분 등을 통해) 고유명사 등을 구별할 수 있는 상황일 것. BUCC2018 shared task에서 SoTA.

* [Bilingual Embedding + Siamese BiRNN](https://arxiv.org/pdf/1806.05559v2.pdf) Bilingual Embedding은 어떻게 잘 train할 것

* [LAZER](https://github.com/facebookresearch/LASER)를 이용한 어프로치. LAZER는 Facebookresearch에서 최근 발표한 라이브러리로 93개 언어에서 트레이닝된 인코더를 제공합니다. [위 말뭉치들 중 WikiMatrix가 LAZER를 이용해 만들어졌습니다](https://arxiv.org/abs/1907.05791).

* [vecalign](https://github.com/thompsonb/vecalign) 와, 작정하고 조지네요. [논문](https://www.aclweb.org/anthology/D19-1136/) 결과는 해 보고 보고합니다.

* [Unihan Database](https://unicode.org/charts/unihan.html) 다른 쪽 언어가 한자를 사용한다면 괜찮은 방법일 수 있습니다. Unihan database는 각 한자를 어떻게 읽는지(한국어, 일 음독, 일 훈독, 만다린 등등등), 뜻은 무엇인지, 간자/정자로는 어떻게 쓰는지에 대한 데이터를 담고 있습니다.

* [JapaneseKoreanNouns](https://github.com/stet-stet/JapaneseKoreanNouns) 제가 만들어놓고 여기 넣기가 쪽팔리기는 한데, KAIST Corpus에 있던 명사 전부를 파파고에 넣고 일본어로 번역한 결과를 정리했습니다. 파파고 특성상 잘못 번역된 단어가 있을 수 있어 주의가 필요합니다.


곧 더 추가됩니다.

# Embeddings

KoBERT 등이 있습니다. 곧 업데이트합니다.

# Ko-Ja specific

아네모네, 꿀도르는 꼭 볼 것
