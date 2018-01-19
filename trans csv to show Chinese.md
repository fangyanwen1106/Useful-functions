import codecs  
import pandas as pd
import numpy as np

%cd E:\Tianchi-Competition\predict TangNiaoBing\dataset

## if csv file cannot show chinese words 
## transfer the unicode

def ReadFile(filePath,encoding):  
    with codecs.open(filePath,"r",encoding) as f:  
        return f.read()  
def WriteFile(filePath,u,encoding):  
    with codecs.open(filePath,"w",encoding) as f:  
        f.write(u)  

## define a function to trans a csv file from gbk to utf_8        
def GBK_2_UTF8(gbkfile,utf8file): 
    content = ReadFile(gbkfile,encoding='gbk')  
    WriteFile(utf8file,content,encoding='utf_8')  
    path = utf8file 
    data = pd.read_csv(path,)  
    return data

## gbkfile = 'd_train_20180102.csv'  raw data in gbk forms
## utf8file = 'd_train_20180102_utf8.csv'  utf_8 forms
train_data = GBK_2_UTF8('d_train_20180102.csv','d_train_utf8.csv' )  
train_data.to_csv('train_data.csv',encoding='utf_8_sig')  
## train_data.csv is the csv file which can display chinese words properly

test_data = GBK_2_UTF8('d_test_A_20180102.csv','d_test_utf8.csv' )  
test_data.to_csv('test_data.csv',encoding='utf_8_sig')  
