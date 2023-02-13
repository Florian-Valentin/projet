## Rapport Séance 7

Lors de cette séance, nous avons trouvé un moyen de faire un lien entre moteur et caméra, le but de ce programme est donc de centrer l'image sur la caméra.
Cependant, en voulant procéder aux ajustements nécessaires sur les dernières lignes du code, notre carte MaixDuino a cessé de fonctionné.
Nous avons tout essayé pour la faire fonctionner, mais un "white screen" constant s'affichait, nous ne pouvions donc pas téléversé le code.
Nous avons désormais tous les élements necessaires.
  -Nous avons crée un réseau neuronale
  -Nous arrivons a faire fonctionner moteurs et caméra ensembles
 Il nous reste donc a aligner la caméra sur le bras moteurs grâce à une structure que nous devrons modéliser.
 
 tim = Timer ( Timer . TIMER0 , Timer . CHANNEL0 , mode = Timer . MODE_PWM )
tim2  =  Timer ( Timer . TIMER0 , Timer . CHANNEL1 , mode = Timer . MODE_PWM )
S1 = PWM(tim, freq=50, duty=3, pin=board_info.PIN1)
S2 = PWM(tim2, freq=50, duty=3, pin=board_info.PIN2)

task = kpu.load(0x100000)
anchor = (1.889, 2.5245, 2.9465, 3.94056, 3.99987, 5.3658, 5.155437, 6.92275, 6.718375, 9.01025)
a = kpu.init_yolo2(task, 0.5, 0.3, 5, anchor)
def  Servo ( servo , angle ):
    S1.duty(((angle*9.45)/180)+2.95)
    S2.duty(((angle*9.45)/180)+2.95)
    time.sleep(0.03)
while True:
        img = sensor.snapshot()
        code = kpu.run_yolo2(task, img)
        if code:
            for i in code:
                print(i)
                a = img.draw_rectangle(i.rect())
        a = lcd.display(img)
        if code:
                # Get bounding box of detected object
                x, y, w, h = code[0].rect()

                # Center of the bounding box
                x = x + w // 2
                y = y + h // 2

                # Move the servo motors to follow the detected object
                Servo(S1,(x - 112) / 112 * 90)
                Servo(S2,(y - 112) / 112 * 90)
                time.sleep(0.03)
