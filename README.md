# 写在前面：
该项目原作者为大佬：
本人只是添加模型验证模块，模块代码来自：
并对部分模型config添加了ngram 词表大小，并修改了部分模型设计的bug，确保程序正常运行，可能存在不合理之处，希望指出。
模型参数文件除了FastText外都已经给出，如果想要使用FastText模型验证的话，需要执行run.py文件。如何训练，后面会写。

## 训练
在终端中输入 python run.py --model 模型名称（比如，FastText）

训练会产生log文件夹（存tensorboard日志）和saved_dict文件夹（存模型参数文件）

## 验证
使用FastText模型 执行eval_FastText.py   

使用其他模型 执行eval.py
  重点！
  这里我偷懒直接用的大佬代码
  所以需要根据使用模型直接在py文件里改代码
  比如，使用TextRNN模型，需要修改：
  18行：         self.args.model = "TextRNN"
  26行：         self.model_name = 'TextRNN'  # TextCNN, TextRNN, FastText, TextRCNN, TextRNN_Att, DPCNN,  Transformer

## 可视化
终端输入 tensorboard --logdir=日志文件的文件夹（我的是 THUCNews/log）
  tips：确保你的path环境里有你的python的scrip文件夹路径，不然不能直接使用tensorboard指令
