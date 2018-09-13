

```bash
$ source activate learn // 切换到之前创建的虚拟环境，以下操作都将在该环境执行

// install Rasa NLU, spacy and its language model for the english language
$ pip3 install rasa_nlu
$ python3 -m spacy download en_core_web_md
$ python3 -m spacy link en_core_web_md en

```