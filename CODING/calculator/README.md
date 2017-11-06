
## Soru İsmi: calculator

## Soru Metni: http://192.168.$MASANO.5:4444/calculator.php sayfasında matematiğimizi ölçüyorlarmış. Sana güveniyorum, bence sen bütün soruları doğru cevaplarsın. 

## Çözüm: 


```python

#!/usr/bin/python

import requests
import time
import base58
import binascii

headers = {'User-Agent': 'Mozilla/5.0'}
URL='http://X.X.X.X/calculator.php'
session = requests.Session()
postdata=""
flag=""

#ilk requesti yaparak Soru 0 i aliyor.
def sendgetreq(session,URL):
	getreq = session.get(url = URL)
	getdataresp= getreq.text
	return getdataresp

# sayfadaki degerleri parse ederek sayilari ve operand i aliyor. Ona gore islemi yapiyor.
def calculate(data):
	number1=data.split("<br>")[4].split(" ")[0]
	number2=data.split("<br>")[4].split(" ")[2]
	operand=data.split("<br>")[4].split(" ")[1]
	print data.split("<br>")[2][3:]+" "+data.split("<br>")[4]
	if operand=="+":
		result=int(number1)+int(number2)
	if operand=="-":
		result=int(number1)-int(number2)
	if operand=="*":
		result=int(number1)*int(number2)

	print "result: "+str(result)	
	return result

	
# calculate fonskiyonunu kullanarak sorunun cevabini hesapliyor ve POST requesti yaparak sunucuya yolluyor ve sunucudan gelen response u aliyor.
def req(question):
	payload= {'input':str(calculate(question)),'submit':'Submit+Query'}
	postreq=session.post(url=URL,headers=headers,data=payload)
	postdataresptext=postreq.text
	postdatarespheaders=postreq.headers
	postdataresp=[postdataresptext,postdatarespheaders]
	return postdataresp

# session expire olmadigi surece bu fonskiyon req fonksiyonunu kullanarak sorunun cevabini gonderiyor ve donen responsetaki headerdaki FLAG degerini aliyor.
def sendresult(postdata):	
	postdataresponse=req(postdata)
	postdata=postdataresponse[0]
	headers=postdataresponse[1]
	print "Cevap "+postdata.split("<br>")[0]+"\n"
	if ("Dogru" in postdata.split("<br>")[0]):
		if (headers.get("FLAG")!=None):
			flag=(headers.get("FLAG")).split("_")[1]
		else: flag=""
	else:
		print "start again!\n"
		print "----------\n"
		flag=""
	return postdata,flag


while "bu son" not in flag:
	#verilen her dogru cevap icin sendresult fonksiyonunu kullanarak header daki flag i aliyor.
	if ("Dogru" in postdata):
		response=sendresult(postdata)
		postdata=response[0]
		flag=flag+response[1]
	else:
		#web sayfasinda "Dogru" bulunmadigi zaman (session expire olduysa ya da yanlis cevap verildiyse) sendgetreq fonksiyonuna gidiyor ve ilk istegi yaparak Soru 0 i alıyor.
		postdata=sendgetreq(session,URL)
		response=sendresult(postdata)
		postdata=response[0]
		flag=flag+response[1]

# flag i base58 decode ediyor.
print "flag: "+flag
flag_hex = base58.b58decode(flag[:-12])
print flag_hex

# hex degeri binary ye cevirerek dosyaya yaziyor ve png dosyasi olusuyor.
fout=open('test', 'wb')
fout.write(binascii.unhexlify(flag_hex))
fout.close()

```
