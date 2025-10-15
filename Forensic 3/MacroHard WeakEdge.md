I've hidden a flag in this file. Can you find it? [Forensics is fun.pptm](https://mercury.picoctf.net/static/c00c449c3b08daaccacca6f9d5c55d49/Forensics is fun.pptm)

# Solucion
Primero hacemos un unzip al archivo de presentacion
```
┌──(diego㉿Tallin)-[~/pico/forensic3/MacroHard]
└─$ unzip Forensics\ is\ fun.pptm 
Archive:  Forensics is fun.pptm
  inflating: [Content_Types].xml     
  inflating: ppt/slideLayouts/slideLayout9.xml  
  inflating: ppt/slideLayouts/slideLayout10.xml  
  inflating: ppt/slideLayouts/slideLayout11.xml  
  inflating: ppt/slideMasters/_rels/slideMaster1.xml.rels  
  inflating: ppt/slideLayouts/_rels/slideLayout1.xml.rels  
  inflating: ppt/slideLayouts/_rels/slideLayout2.xml.rels  
  inflating: ppt/slideLayouts/_rels/slideLayout3.xml.rels  
  inflating: ppt/slideLayouts/_rels/slideLayout4.xml.rels  
  inflating: ppt/slideLayouts/_rels/slideLayout5.xml.rels  
  inflating: ppt/slideLayouts/_rels/slideLayout6.xml.rels  
  inflating: ppt/slideLayouts/_rels/slideLayout7.xml.rels  
  inflating: ppt/slideLayouts/_rels/slideLayout8.xml.rels  
  inflating: ppt/slideLayouts/_rels/slideLayout9.xml.rels  
  inflating: ppt/slideLayouts/_rels/slideLayout10.xml.rels  
  inflating: ppt/slideLayouts/_rels/slideLayout11.xml.rels  
  inflating: ppt/theme/theme1.xml    
 extracting: docProps/thumbnail.jpeg  
  inflating: ppt/vbaProject.bin      
  inflating: ppt/presProps.xml       
  inflating: ppt/viewProps.xml       
  inflating: ppt/tableStyles.xml     
  inflating: docProps/core.xml       
  inflating: docProps/app.xml        
  inflating: ppt/slideMasters/hidden  
```
Despues vemos que esta el archivo hidden, podemos hacerle un cat
```
┌──(diego㉿Tallin)-[~/…/forensic3/MacroHard/ppt/slideMasters]
└─$ cat hidden  
Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q   
```
Podemos quitar los espacios y decodificarlo de base64
```
┌──(diego㉿Tallin)-[~/…/forensic3/MacroHard/ppt/slideMasters]
└─$ cat hidden | tr -d ' '| base64 -d
flag: picoCTF{D1d_u_kn0w_ppts_r_z1p5}   
```