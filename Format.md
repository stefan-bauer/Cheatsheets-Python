# Copy all Jupyter Notebooks to Markdown


```python
import os
```


```python
def convertInMarkdown():
    pth='./'
    files = [f.split('.')[0] for f in os.listdir(pth) if os.path.isfile(os.path.join(pth,f))and f.split('.')[1] =='ipynb']
    print('The files in this folder are: {}'.format(files))
    
    for file_idx in range(len(files)):
        print(files[file_idx])
        os.system('jupyter nbconvert --to markdown {fn} --output "../Markdown/{fn}"'.format(fn=files[file_idx]))
```


```python
dirs=[dir for dir in os.listdir('.') if os.path.isdir(dir) and dir[0] != '.' and dir != 'Images']
```


```python
for idx in range(len(dirs)):

    os.chdir('{}/Jupyter_Notebook'.format(dirs[idx]))
    print('Changed into folder: {}'.format(os.getcwd()))

    convertInMarkdown()
    
    os.chdir('../')
    os.chdir('../')
    print('Im in folder: {}'.format(os.getcwd()))

```


    ---------------------------------------------------------------------------

    FileNotFoundError                         Traceback (most recent call last)

    <ipython-input-10-7c6cc7313642> in <module>
          1 for idx in range(len(dirs)):
          2 
    ----> 3     os.chdir('{}/Jupyter_Notebook'.format(dirs[idx]))
          4     print('Changed into folder: {}'.format(os.getcwd()))
          5 


    FileNotFoundError: [Errno 2] No such file or directory: '02_DataScience/Jupyter_Notebook'



```python
os.getcwd()
```




    '/home/stefan/Work/Github/contact/Cheatsheets-Python'




```python
import os

path=os.path.abspath(".")
print(path)
```

    /home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python



```python
for root,dir,files in os.walk(path):
    for file in files:
        if(file.endswith('.ipynb')):
            apath=os.path.join(root,file)
            apath_list=apath.split('/')
            aps=apath_list[-1].split('.')
            apath_list[-1]=aps[0]
            try:
                i=apath_list.index('Jupyter_Notebook')
                apath_list[i]='Markdown'
                thePath='/'.join(apath_list)
                os.system('jupyter nbconvert --to markdown {fn1} --output {fn2}'.format(fn1=apath,fn2=thePath+'.md'))
                print(thePath)

            except:
                thePath='/'.join(apath_list)
                os.system('jupyter nbconvert --to markdown {fn1} --output {fn2}'.format(fn1=apath,fn2=thePath+'.md'))
                print(thePath)

```

    /home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/Format copy
    /home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/Format



```python
os.system('jupyter nbconvert --to markdown {fn} --output "../Markdown/{fn}"'.format(fn=files[file_idx]))
```
