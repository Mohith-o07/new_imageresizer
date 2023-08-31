source code:<br># new_imageresizer<br>
    print("****This tool currently only works for images with the extension .jpeg****")<br>
    source = input("enter the path of the source folder in which the images are present:")<br>
    destination=input("enter the path of the destination folder to which the resized images has to go:")<br>
    source=os.path.join(r"{0}".format(source)) #maps the source to the folder in the system <br>
    destination=os.path.join(r"{0}".format(destination)) #maps the source to the folder in the system <br>
    scale = int(input("Enter the scaling factor [between 10-90]:")) <br>
    j=random.randint(1,100000) <br>
    for i in os.listdir(source): <br>
        src = cv2.imread(os.path.join(source,i)) <br>
        #cv2.imshow("image",src) <br>
        new_width = int(src.shape[1] * scale / 100) <br>
        new_height = int(src.shape[0] * scale / 100) <br>
        output = cv2.resize(src, (new_width, new_height)) #resized image <br>
        des="newimage{0}.jpeg".format(j) <br>
        cv2.imwrite(des,output)   #output is stored in des <br>
        j+=1 <br>
    images=[f for f in os.listdir() if '.jpeg' in f.lower()] #resized images that are stored in the 'current' folder are added to the list <br>
    for image in images:    <br>
        new_path=destination+"\\"+image <br>
        shutil.move(image,new_path)  <br>
    print("VOILA! IMAGES are successfully RESIZED!") <br>
