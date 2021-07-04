# Face_recognition
İmport cv2
import os          

cam = cv2.VideoCapture(0)      
face_cascade =    cv2.CascadeClassifier("/home/pi/Documents/haarcascade_frontalface_default.xml")
global user   
 
user = input("kullanıcı adı girin")   
 
print(" \n [!!UYARI!!] Kameraya bakın ve bekleyin ...")

os.mkdir(user)   

i=0  
 
while (True): 
 
    ret,frame=cam.read()  
     
    frame=cv2.flip(frame,1)   
  
    gri= cv2.cvtColor(frame,cv2.COLOR_BGR2GRAY) 
  
    faces=face_cascade.detectMultiScale(gri, 1.5, 3)
    for (x,y,w,h) in faces:
        cv2.rectangle(frame,(x,y),(x+w,y+h),(0,255,0),2)
      
       
 i+=1      
   
path:"/home/pi/python/"+user+"/"    
        cv2.imwrite( "path" + str(say)+ ".jpg",gri[y:y + h,x:x + w])
        cv2.imshow("kayit_ekrani",frame)
       
    if cv2.waitKey(5) & 0xFF==ord("q"):  
        break
    elif say>= 100:  
        break          

cam.release()
cv2.destroyAllWindows()

