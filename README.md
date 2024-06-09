# 中文文本分类项目

## 写在前面

该项目原作者为大佬：[@huwenxing](https://github.com/649453932)  
项目地址：[Chinese-Text-Classification-Pytorch](https://github.com/649453932/Chinese-Text-Classification-Pytorch)  
本人只是整合代码，添加模型预测模块，模块代码来自：[@maoding1](https://github.com/maoding1/sinaCrawler/blob/master/eval.py)  
并对部分模型config添加了ngram词表大小，并修改了部分模型设计的bug，确保程序正常运行。可能存在不合理之处，希望指出。

## 训练 验证
在终端中输入
```
python run.py --model 模型名称（比如，FastText）
```
  如果你的编译器和我一样对这个指令没有反应，可以直接需改run.py文件（上面的指令ok就别改了），手动执行，有点麻烦：
  修改代码 12行：
  ```
  parser.add_argument('--model', type=str, required=True, help='choose a model: TextCNN, TextRNN, '
                                                                                 'FastText, '
                                                                                 'TextRCNN, '
                                                                                 'TextRNN_Att, DPCNN, Transformer')
  ```
    tips： 添加参数default=“训练模型名”，required=False
  ```
  parser.add_argument('--model', type=str, default=“训练模型名”, required=False, help='choose a model: TextCNN, TextRNN, '
                                                                                 'FastText, '
                                                                                 'TextRCNN, '
                                                                                 'TextRNN_Att, DPCNN, Transformer')
  ```
训练会产生log文件夹（存tensorboard日志）和saved_dict文件夹（存模型参数文件）

## 预测
使用FastText模型 执行eval_FastText.py   

使用其他模型 执行eval.py
 重点！
  这里我偷懒直接用的大佬代码
  所以需要根据使用模型直接在py文件里改代码
  比如，使用TextRNN模型，需要修改：
  ```
  18行：         self.args.model = "TextRNN"
  26行：         self.model_name = 'TextRNN'  # TextCNN, TextRNN, FastText, TextRCNN, TextRNN_Att, DPCNN,  Transformer
  ```
## 可视化
终端输入 
```
tensorboard --logdir=日志文件的文件夹（我的是 THUCNews/log）
```
  tips：确保你的path环境里有你的python的scrip文件夹路径，不然不能直接使用tensorboard指令


