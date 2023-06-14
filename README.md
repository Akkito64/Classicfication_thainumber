# Classicfication_thainumber
## Introduction
วัตถุประสงค์ : ให้สร้าง Classificaition model จาก handwritten number โดยไม่ใช้ deep learning เช่น CNN หรือ library Keras
## 1. Data Collection
1. ทำการรวบรวมจากการเขียนโดยใช้ program paint หรือ อื่นๆที่สามารถเขียนได้ โดยมีข้อกำหนดดังนี้

    1.1.1 Images of handwritten Thai numbers from 0,1,2,...,9, along with their associated labels.
    
    1.1.2 Image width and height: 28x28 pixels
        - Background color: "white"
        - Font color: "grayscale"
        - ![image](https://github.com/Akkito64/Classification_thainumber/assets/110782963/6dbe9630-ecbf-42eb-80f0-7fb1eae6700a)

    
## 2. Data cleansing
เราจะทำการเปลี่ยนให้เป็น Grayscale

![image](https://github.com/Akkito64/Classification_thainumber/assets/110782963/81e9cb41-86c2-464d-8562-bd7cf3bd6fc8)
ทำการเปลี่ยนรูปร่างโดยการตัดขอบเพื่อให้ model มีความแม่นยำมากขึ้น

![image](https://github.com/Akkito64/Classification_thainumber/assets/110782963/6090cf47-eb27-4b7c-9c93-ae48cbe5d3e5)

## 3. EDA
```x_train, x_test, y_train, y_test = train_test_split(data, labels, test_size=0.2, random_state=42, stratify=labels)```

1. มี traning sample และ test sample อย่างละเท่าไร
2. รูปภาพมีขนาดเท่าไร
3. สัดส่วนของเลข 0-9 ในแต่ละเลขเป็นเท่าไร

![image](https://github.com/Akkito64/Classification_thainumber/assets/110782963/5b17d104-1251-48c7-8796-58df59df63e6)

![image](https://github.com/Akkito64/Classification_thainumber/assets/110782963/844e6ca0-3b79-46f9-9521-e69c36d13466)

![image](https://github.com/Akkito64/Classification_thainumber/assets/110782963/79bde49a-494b-4173-af42-a919be306214)

## Training 
เป็นวิธีเพื่อหา model ไหนมีความแม่นยำมากที่สุด ในที่นี้เราจะใช้ pycaret(AutoML) ศึกษาเพิ่มเติ่มได้ที่ https://pycaret.org/

แล้วเราก็ทำการดูว่า model ไหนมี Accuracy หรือ F1 score มากที่สุด ศึกษาเพิ่มเติม https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9

โดยเราจะยก model มา 3 ตัว คือ ExtraTreesClassifier , LogisticRegression , RandomForestClassifier ตามลำดับ โดยในแต่ละการ Excute ในแต่ละรอบจะมีค่าที่เปลื่ยนไปตลอด

## Testing
โดย model ที่เราจะใช้ test ก็คือ LogisticRegression

ผลที่ได้ ความแม่นยำอยู่ที่ 0.900

![image](https://github.com/Akkito64/Classification_thainumber/assets/110782963/e5e7df37-b758-4bcd-8e6c-9a7423234dbf)


## Evaluation metrics
ผลที่ได้คือโดยดูจากกราฟ AUC Curve และ Class report

![image](https://github.com/Akkito64/Classification_thainumber/assets/110782963/07d1a017-d668-44a5-a73a-7e19761ea882)

![image](https://github.com/Akkito64/Classification_thainumber/assets/110782963/ba4a9418-2a87-4020-b3b0-9d8c0d4267f1)

![image](https://github.com/Akkito64/Classification_thainumber/assets/110782963/a73c3c45-6736-4b4b-a1c3-8d8714bbffcc)





สรุปได้ว่าผลที่ได้มีความแม่นยำอยู่ในช่วง 0.8%-1.0% ถือว่าได้ค่าที่แม่นยำมาก


## สิ่งที่ต้องปรับปรุง
1. ค่าที่ได้อาจจะไม่ถูกต้อง 100 % เพราะว่า มีข้อมูลที่น้อยเกินไป อาจจะทำให้ model overfitting
2. ในการแบ่งแยก image Classification ในการเลือกใช้ model อาจจะต้องใช้ CNN (Convolutional Neural Network)  










