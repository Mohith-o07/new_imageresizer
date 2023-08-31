source code:# new_imageresizer
    print("****This tool currently only works for images with the extension .jpeg****")<br>
    source = input("enter the path of the source folder in which the images are present:")
    destination=input("enter the path of the destination folder to which the resized images has to go:")
    source=os.path.join(r"{0}".format(source)) #maps the source to the folder in the system
    destination=os.path.join(r"{0}".format(destination)) #maps the source to the folder in the system
    scale = int(input("Enter the scaling factor [between 10-90]:"))
    j=random.randint(1,100000)
    for i in os.listdir(source):
        src = cv2.imread(os.path.join(source,i))
        #cv2.imshow("image",src)
        new_width = int(src.shape[1] * scale / 100)
        new_height = int(src.shape[0] * scale / 100)
        output = cv2.resize(src, (new_width, new_height)) #resized image
        des="newimage{0}.jpeg".format(j)
        cv2.imwrite(des,output)   #output is stored in des
        j+=1
    images=[f for f in os.listdir() if '.jpeg' in f.lower()] #resized images that are stored in the 'current' folder are added to the list
    for image in images:
        new_path=destination+"\\"+image
        shutil.move(image,new_path)
    print("VOILA! IMAGES are successfully RESIZED!")
