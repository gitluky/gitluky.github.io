---
layout: post
title:      "The cliffnotes on Classes and Objects"
date:       2019-02-25 23:12:10 -0500
permalink:  the_cliffnotes_on_classes_and_objects
---


Classes and objects are essentially the foundation of Object Oriented Programming. I have been working with them for a while a now and don't really put much thought into it while I'm smashing out new code on my keyboard anymore. But in the beginning when I was first learning it, it was a bit daunting. I felt I've reached a huge revelation - Morpheus had just given me the red pill and shown me how I should really be looking at the world. Instead of viewing everything as a continuous sequential stream of code, everything is viewed as separate objects modelled after the real world...people, cars, building, the woman in the red dress, etc. Let's dive deeper into the rabbit hole, and that!...will be the last of Matrix references. 
A simple way to look at it is that the class itself is the blueprint as well as the manager for creating the objects (instance of the class, instance and object will be used interchangeably here). A class is blueprint, as in, it defines all the attributes the object has and things it can do(methods). For an example, given a Car class, the class Car itself is like the car factory and the purpose of this class is to provide a blueprint to make objects, specifically cars, as well as manager all the cars in its inventory. It will define all the instance variables to store information on each car such as make, model, color, type, transmission…anything really. Instance methods will be defined to interact with these instance variables and also allow the car to do things like turn, honk, accelerate, brake...yada yada yada. 
That might have been confusing, but let’s go through the works. This is how you define a class:
![](https://lh3.googleusercontent.com/D8im1XvNKYxYBkwxGzgLtcG2pWmWa5PWKhg-btvhFQaAbhO3V2fcJlOT-84BMDXtxROis-S3C_UPzRgbJUxqQQMT4PbZyZU5-hCS8P7pmWlGeAPAF-KDSiRKsb0YeNYyMX-zMJe8dABkYR-TjFlPk656JxczYYxyGbrocDNPpflEAeLAKOEFclcp_lCuTEGN4RiH2IdOzSieAp50nMZDAqpduNVzCq97Or16buy8dy7RsvBgal-54jOYGrGJ4-PZCp1kLigMW2HWZgnJg_0J9MQqhR5ZIz44bJDBhtu21Di841OMn8hxSiHNfY4_eaS41faL4599at25ao_DFoEoZbrFahqKyoiDzJEBVSr6fjhWc2WOEawjfDryAvsMWMtQL8MMHRKz-DZYcFQ74RUSX2lbXbKdXBMeZSZ1k9z85j7dn9Vd3zYKAlS8doFzlJ4dHX5C6APCEhkKMsjTxmQA9-NoEjeYovdpqFj4rdnposSnbeNZT902hWCtZ1souimj2A0KscA_QghA7UNJZIwsyPBr9WzM9DxUkp1EIJhWxZZPAnxeuU2Eef2c6Vk56PWvi8JLVB1xzOd7p3t1J7sqbt6o2aHd0AyJ5cuSwOTuMd129592Ut4d66CqQ7n2PnSU6x9gjpaEHbvm0R4HayYYls2HXP8wzEo=w523-h62-no)
Figure 1

Awesome! We have a car class, an empty a Car class, but a class nonetheless. 
To create (instantiate or initialize) a car, we tell the class to make one:
 ![](https://lh3.googleusercontent.com/85-Y3DrnSz3CHe--VgqfpJetYBNJGoz7p2bEY_Jbr2J1JNSVnPHaDtu7b5ZBdnQDqvyfzFGca0l-W0z5jmy-5f05f9P2YJKAQlne-PsD1DIxhCnCcYGKiD9yDERcmy4wZjOJOBT4lsnzXO09GR2fmD9bKJi3xeHiTFjkCZrKpyM6N8W9eYnChTq2DCZCDNbPSfC7d3vexiWTXvQa8Dv4mvrjVqW-sbfH3SeDSDK-BOdwGfPg8I52fObhi_rZch1SjTV9XXfCEYgYD66aI98a41mXQ9erQYuMCKBQuSpuISX7s7BULiQ3b43__qSVKSMPfPm3i0KDZPbeoCeABOcEbAId8aV2-fn8rbGlB2XGBFTSigi5o7ojuGjeLOyeFdsAr_RUAVeJ5AgYrBMM-_if6xjum8Gipavb37EuDVvqHPx85sG3Y3cJx5VI0hnIAqFbn1NX4a6hjmCPohavpUYZVb2YMsk4Q_6rXP9mp7YlMys2EpGFO86Fxz1WV-1BPPCkKfMSs10a-Vx03cqRLJb6M3i6MQpk4f_iNIOxoG8--FEW3uRedu8ERZwdEJfwy-6D8jCAxjAVkSOwg6f422D2kis1ufYhJ4KozIzk4ylkhncKXAFWolkkwDh-znKhImiy8D1VJi3-ieDnrz6eGZS06Q2NJaZi_Gc=w520-h24-no)
Figure 2

In this case, we’ve created a new car and assigned that car to the variable car_1. As of now, we haven’t given the car and attributes or methods so it’s pretty useless, but shown below in Figure 3 and Figure 4 is we want to be able to do with our car - set attributes for the car and get them when we want them.
Setting instance variables:
 ![](https://lh3.googleusercontent.com/aXVLGu02XXM96qowwFeszMGBTZDEABXWd8vROOy70dgFcsGI-g1kpmVUEQ8rkn7pi11Nxy1kFGbC3MtanITyn5YEbvKWNJl4VwYBcv7eJk1torirMLMpMsYGHCzCGQJfYy0Aq6sVX2Wwx1v263gJ72XJDP4A8XlXesLV4bh_yJPljXeyfRS8t_bjTRLmRmjVQSFhimQzhnHZwSyvhZzpwojgX7Ex_Aat6vXWCvnFuGwSWm_geguyZ6eEote6SRZnOBN1KZq6rr7ucI8lU37ihPyNq77mrP4ncr986HKRO39FoU21fesgSkxlo7pogj8tx4Rj-jlfMkEN9cGDMgGu7yOkhkDVssBLdulbrGWyDLEFQwPD7FIamxGsN3Tva2xD7o8sgtt9eAyqBKlxfJlp-sW1mydQxovN6WhTwDbkMnE3W8W-YOr9u6D5H-hJl24yhyNPpsGJRmubmCpKLLNov8PLGIoSRbh0FLB-gWt-D3XHYdTglmc2NKPFj9ZwmMg29is-9BigWRvA2KegNw9kFRljTq11XbKUyo0dsnNkC9vfbLqe0yYdG9mIUgeRc3ORo7BtP9jF4emqwxARWSmIS2IAKBQ0m3UgB09VMXb2YxhwdqXTsI4DqYdn7t2JhopWThNZ4GD6czcDROTqjHp69yXSrL7kjUg=w527-h60-no)
Figure 3

And calling the instance variable to get the attributes for the car:
 ![](https://lh3.googleusercontent.com/miS3nfZg6X_XUaAfl6U9z64V7R2XjkOTp_S_c3zLICVaZk4t54Ru08u1NyNg8W0v-fcAimC8HwwClZdCbceVHbSe-Xz-zXSC35LgQx7L7xtb8c2aORUvjNah2rugfEO5338tI_6Q-bgzF3IonTE4ynXsa1kmy24BgA_LfiO8dt4P1DBI5B96ph3q43L-EsSGUfiEiNhsvIR9fgr0njcyjkbkoe5ZArjlo0BLm8vlDKRNnubbvSRX5-s2Xd7NTs72PRjYRm9M15z_8AnGLZtOdy6iyhtMtMYciETzkZg46xt0VOS8DG2VMVajurEjQsDvC-9bMf3jY8lLRQw9fN49096GyFoULZDfLoIhhPE67p5Uh7RaFsIqOuusub36LnFIzClabG9pnZu4XtaBYwSspq_WqPUQvNj0EPY3zEaHV7SxhyKA5_mQcYyOl8g3P7692FWySp3lHtPY7m5j0IjHbNcCwCvomNOeSuv3Au9HrFa-lb2vsKs1xswGahXGcmIriqic376F5srYaEnz0xoFegOpWm495qVRZLdGjsU6fohwdZWOzwppoyYslD28WAfe5dhOmFCIY30Rft091mFkt72FxCalQSnRDnreKNA5fkgGlPa6g2-f-T8f2f5dcexvFtSEuAaIwRew4cCrOT99HKRdJhGQLJo=w538-h38-no)
Figure 4

To be able to do this, instance variables have to be defined:
 ![](https://lh3.googleusercontent.com/KQ-tSuXY5msc6gEp0rkIM68tZodd6Z0eIKE9GA4OCWlVkKshr1DfuGjcUQLM5oI4zVrRQuiDGyyxD3KfIdWQuFaEYgdH1ACY5YuN6xRvf63UYAD9s5nSdGIC-1Lyy4HSSriZ2wIA640FWAbvTET7KcDcbEB4B_jcKLg5nIptN2hFmoXY_8si_0ZnS35pbnI3yu01tAL1FDEopYETZTie3f_vFMrfd4FU2ma6O3pxUO72ZaetgcV-bCsoEfk6MLoNG5l7Wc3daw9Fb_Cwauq1KAUCY1COLofZpvXSFuiSxcHPfUrRZFvdGjanm5Vbbj1L92RtSvMo0-BCe9L3_3vb4MtUTBcN2z-dPI3JPVnfTnBx3Givv7fdRDS_tqgoSFvo_2uTHFxZBvp1kgBeYu24ai3ib6-A1_lu-aQiVkPNvHK6TFxt2caFE3KiELqBBs9BRmkU0Yi0CnJ9C-l5FUPCwbt8JOmG0x_A9nkLTs-jETwsko68BKE1w-_9hR98_OcZwYaAyaMD4OZYEzXBF19LTB9MldMaDnmygiJ6hWVCFW6OGIVnIiJBDkfRRJLjwSAGpEne9xc2wLm0xfFdgw1MW-PMSL6w594nHr98SxMJOjq-umnZScd3EcEJqGN0_EsPpO4sruHa0QWjglOHpIlKyFDkWWaorUsnNmXDiWpSSEPEtSB0GeKNm3foOX1zYnagll2iKI9kB_AhhsB1qPn0VeGF=w529-h173-no)
Figure 5

Instance variables have a @ in front of them, to differentiate from local variables which cannot be used across instance methods; the scope of local variables will be contained in the scope in which they are defined while instance variables can be called from all the instance methods. Before we can start interacting with the instance variables like we did in Figure 3 and Figure 4, we need to create some instance method. In Object Oriented Programming this is either called getter and setters OR readers and writers because they’re made to do just that. When we write car_1.make = “Honda”, we are actually calling a method called make= on car_1, to set the value to “Honda” and when we want to get the make that is set, we need a get method, make, to call on car_1 to reveal the instance variable to us.
![](https://lh3.googleusercontent.com/Lh2FiIKZeQ3vazHTPG9b4l3tQ4kwNCrQyevf9AlpI3lI--3x-Lw6q4JA8aZbEIJoRS4TDyUvZNJRlQjTyY-xooezpfgHYuHbRVYPbqoXwV3V3yVwdlNmTPl8kKQUO9MJ4dWTMFBORTuaZGdXMxdAbcRaZFY6nP8dggaSts6z_MA2ZuCAp1lOSNfH4PswBvZ9IBQ3q_iwePauvA6teNPzFSEV-_p3dCsFBg0-y0ZIg7GeWg-65J-WJw7mBAdqEG5q8HQu_69E-IJHUjSjCpDn0rmCauZ6InNNOyuRe8jj0ivZ2mf5V59k4zGgZdeYbG1egGh-FWlS3uv42SrZ1xUeKNesYJVk6IcEOTw5rJ_E8b4ciChlINsk_xVMYBlabUWS4BMuFja-npEbyrLcSF5emxnc5XItaKRwQYQJgOKBHBCy9YdX0Y1dz9Lv6_Q8RLYwaZ9RjxqDv7RHZ-I4OWwH3fQ6DfbH-wKN6DybZ4CQdh4qjYzxyn_yRDYl6S2Qwrxa7VVg-GYGnvSz5BEqjsFGAmxrUsOpLaz32eLCCi7Uq8NyOHq_kW3h4zFO-uzZa1qPG4iKaYDvgt56oKd3BbD6uKvYHwsxDYSYC5os-IZgpHUZsEMVOErljqNun4q3Dr5xJCr3E8axhoUFLWbnRPHnCt6HiQrpJds=w529-h484-no)
Figure 6

There should be a getter and setter for each instance variable that you want to be able to read and write to. We only have them created for 2 of the instance variables so far, and as you can see, it can easily add up to a lot of typing, and as programmers, we’re lazy, so luckily Ruby has made it simple for us, we simple have to write attr_accessor followed by the instance variables we want setters and getters for.
 ![](https://lh3.googleusercontent.com/kTuoIZ_eJe6r5227iN4BVjRpbGM4pcfRJyv2jmFp90pPzzg5cGss3AwCHXUawUBlas3pFfq_t3nCwfYyKaxZR_HDv6820b7xiz7P_9EtreFuZNO23annEsI0FdS_KPG0TWNKhKk54IpD9ljGH-5zHF6yqVT-lQ8OIFfdrxOSJ946mkLG1Imd11-6IT-KZlhMhIHZYDGTIa_QfRaQ96vU7cfRVU1XwKMyq24MmrZRxT5Ub9vVqdK0yuxShlQW6E2igsHwLk5YeKVcRXknAaXHMLfWiyWbros5p48hp0FSiiNjaf-htl2l-AlQ53cD6Av23Z49q-vVKMN-ftgVWZOUxZls2TqE7I9z-Sjp9BvBrz94mDA1YVypJ_chO9Lc9PGFRGT6NowNbQb9b79qjqrNAqWfr2-EjHeUwJ1Jm1Z6AA0nC9dhayc7_zuXap7_SDCMqdAnBVr24rJKaUZOYsAXfWFE1j-ePtDF-x8KHHhQAaf9VQZKQmmeJRquguRQwDKbURwuBK0ArsSGKbcWhoc142WM8SYjzN_BYZ5o2I6O6LCArKP3QET4bJZlW-Yvq3Zw6QSsmABLBj-BIXqQtdbKez-6SbeDzgqlBmGVkjbhZPKc6GOtjRJ5fhlSM66g1rk5q8XI79xeu91CIwb0-ktEU9M7jti1KG0=w528-h98-no)
Figure 7

Figure 7 is exactly same as Figure 6 except with setter and getter methods created for all the instance variables. 




