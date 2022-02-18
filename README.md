# facebookstreaming


import urllib

import requests
import os
import re
import sys
host = "192.168.1.8"
port = 22
username = "imac"
password = "Iphonexr2022"


#page bouazza
#page_id = "346953866407497"
app_id = "647732946349357"
client_secret = "1704606fdb35837951a3aed996faa3f9"
user_id="797337521193246"
string = ""

#page  https://www.facebook.com/aymtv1
page_id ="516306001798180"


access_token = "EAAJNHBQtLS0BAAd45n2wldLp7IONbQ3JUWhNZCc6a2zJmi3qGYvvPLrgmhtnRFXRr0vxU0eFSSUxENHkScYE5ZA712OBNw4aDiFW4xHvkq7PxsyfnZBPW80XZCQSADddVEoq8VaB1NQvJ0ezZC7FgnK9HiLqM3ZBYMt6EHSaJCNnsGTNlhIj916TkfbBZCNFCIs5npI9o1XCit8kjEhexkaNJjW9JZAdgpVLr6YjZAlRVGNuuRS029epR"
access_tokenP = sys.argv[1]
title = "البث المباشر لقناة مدي 1 تي في"

utf8_strt = title.encode("utf-8")
titlef = utf8_strt.decode("utf-8")


description = "تتابعون الآن البث المباشر لقناة مدي 1 تي في"

utf8_strd = description.encode("utf-8")
descriptionf = utf8_strd.decode("utf-8")

url2 =f" https://graph.facebook.com/{page_id}/live_videos?status=LIVE_NOW&title={title}&description={description}&access_token={access_tokenP}"
print(url2)
ffmpegCode  = "ffmpeg -re -i udp://51.222.88.198:6974 -vcodec copy -b:v 2950k -preset ultrafast -acodec aac -async 1 -b:a 128k -ac 2 -ar 44100 -f flv -muxrate 1300k rtmp://192.168.1.8:1935/live/medi1tv &"
nodeCode = "node /Users/imac/rtmp/app1.js"



r = requests.post(url2)
data = r.json()

print(data)
link= data["secure_stream_url"]
print(data["secure_stream_url"])



#os.system("nohup /usr/local/bin/node /Users/imac/rtmp/app1.js &")

os.system(f"ffmpeg -re -i udp://51.222.88.198:6974 -vcodec copy -b:v 2950k -preset ultrafast -acodec aac -async 1 -b:a 128k -ac 2 -ar 44100 -f flv -muxrate 1300k '{link}' ")







