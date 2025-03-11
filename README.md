# first-app
import 'package:flutter/material.dart';


void main() {
  runApp(BMICalculatorApp());
}

class BMICalculatorApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(debugShowCheckedModeBanner: false,
      title: 'BMI Calculator',
      home: mm(),
    );
  }
}

class aa extends StatelessWidget{
  const aa({super.key});
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: ms(),
    );
  }
}


class ms extends StatefulWidget{
  const ms({Key? key}) : super(key: key);

  @override
  _msState createState() => _msState();
}

class _msState extends State<ms> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(appBar: AppBar(
      centerTitle:true ,title: Text('BMI',style: TextStyle(color: Colors.white),),
      backgroundColor:  const Color.fromARGB(255, 47, 48, 48),
    ),
      body:
          Center(
            child: 
              Column(crossAxisAlignment: CrossAxisAlignment.center,
                children: [                SizedBox(height: 30,),
                  Text('Your Results',textAlign: TextAlign.start,style: TextStyle(fontSize: 25,color: Colors.white),),
                SizedBox(height: 30,),
                  Container(height: 450,
                  width: 500,
                    decoration: BoxDecoration(borderRadius: BorderRadius.circular(10), color: const Color.fromARGB(255, 46, 59, 66),),
                    child: 
                      Column(crossAxisAlignment: CrossAxisAlignment.center,
                      mainAxisAlignment: MainAxisAlignment.start,
                        children: [SizedBox(height: 50,),
                          Text('${mm.BMICategory}',style: TextStyle(fontSize: 40, color: Colors.greenAccent ),),
                          SizedBox(height: 50,),
                          Text('bmi ${mm.BMI}',textAlign: TextAlign.center,style: TextStyle(fontSize: 40,color: Colors.white),),
                        ],
                      ),
                  ),
                  SizedBox(height: 40,),
                  InkWell(
                    onTap: () {
                      Navigator.push(
                          context, MaterialPageRoute(builder: (context) => mm()));
                    },
                    child: Container(
                      height: 60,
                      width: 200,
                      decoration: BoxDecoration(color: Colors.pinkAccent, borderRadius: BorderRadius.circular(10)),
                      child: Column(mainAxisAlignment: MainAxisAlignment.center,
                      crossAxisAlignment: CrossAxisAlignment.center,
                        children: [
                          Text('Recalculate',style: TextStyle(fontSize: 20),),
                        ],
                      ),
                    ),
                  )
                ],
              ),
          ),

      backgroundColor: Colors.black,
    );
  }
}

class mm extends StatefulWidget {
  @override
  mmm createState() => mmm();
  static double BMI = 0;
  static String BMICategory = '';
}

class mmm extends State<mm> {
  int height = 170;
  int weight = 60;
  int age = 24;
  bool isMale = true;
  double bmi = 0;
  String bmiCategory = '';
  void calculateBMI() {
    double heightInMeters = height / 100;
    bmi = weight / (heightInMeters * heightInMeters);

    setState(() {
      mm.BMI = bmi;
      if (bmi < 18.5) {
        bmiCategory = 'Underweight';
      } else if (bmi < 25) {
        bmiCategory = 'Normal';
      } else if (bmi < 30) {
        bmiCategory = 'Overweight';
      } else {
        bmiCategory = 'Obese';
      }
      mm.BMICategory = bmiCategory;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('BMIcalculate',style: TextStyle(color: Colors.white),),
        centerTitle: true,
        backgroundColor:  const Color.fromARGB(255, 47, 48, 48),
      ),backgroundColor: const Color.fromARGB(255, 47, 48, 48),
      body: Column(
        children: [
          Expanded(
            child: Row(
              children: [
                Expanded(
                    child: GestureDetector(
                  onTap: () {
                    setState(() {
                      isMale = true;
                    });
                  },
                  child: Container(height: double.infinity,
                    color: isMale ? Colors.pinkAccent : Colors.black,
                    child: Row(mainAxisAlignment: MainAxisAlignment.center,
                    crossAxisAlignment: CrossAxisAlignment.center,
                      children: [
                        Text(
                          'Male',
                          style: TextStyle(color: Colors.white, fontSize: 30),
                          textAlign: TextAlign.center,
                        ),
                      ],
                    ),
                  ),
                )),
                Expanded(
                    child: GestureDetector(
                  onTap: () {
                    setState(() {
                      isMale = false;
                    });
                  },
                  child: Container(height: double.infinity,
                    color: !isMale ? Colors.pinkAccent : Colors.black,
                    child: Row(mainAxisAlignment: MainAxisAlignment.center,
                    crossAxisAlignment: CrossAxisAlignment.center,
                      children: [
                        Text(
                          'Female',
                          style: TextStyle(color: Colors.white, fontSize: 30),
                          textAlign: TextAlign.center,
                        ),
                      ],
                    ),
                  ),
                )),
              ],
            ),
          ),
          Expanded(
              child: Container(
            child: Row(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Slider(
                  value: height.toDouble(),
                  min: 100,
                  max: 250,
                  onChanged: (value) {
                    setState(() {
                      height = value.round();
                    });
                  },
                ),
                Text('$height cm'),
              ],
            ),
          )),
          Expanded(
            child: Row(
              children: [
                Expanded(
                    child: Container(
                  decoration: BoxDecoration(
                      color: const Color.fromARGB(255, 46, 59, 66),
                      borderRadius: BorderRadius.circular(10)),
                  child: Column(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: [Text('Weight', style: TextStyle(fontSize: 20,color: Colors.white),),
                      Text('$weight', style: TextStyle(fontSize: 20,color: Colors.white),),
                      Row(crossAxisAlignment: CrossAxisAlignment.center,
                      mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                          IconButton(
                            icon: Icon(Icons.remove_circle_rounded, color: Colors.white),
                            onPressed: () {
                              setState(() {
                                weight--;
                              });
                            },
                          ),
                          IconButton(
                            icon: Icon(Icons.add_circle_rounded,color: Colors.white),
                            onPressed: () {
                              setState(() {
                                weight++;
                              });
                            },
                          ),
                        ],
                      ),
                    ],
                  ),
                )),
                Expanded(
                    child: Container(
                  decoration: BoxDecoration(
                      color: const Color.fromARGB(255, 46, 59, 66),
                      borderRadius: BorderRadius.circular(10)),
                  child: Column(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: [
                    Text('Age', style: TextStyle(fontSize: 20,color: Colors.white),),
                      Text('$age', style: TextStyle(fontSize: 20,color: Colors.white),),
                      Row(crossAxisAlignment: CrossAxisAlignment.center,
                      mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                          IconButton(
                            icon: Icon(Icons.remove_circle_rounded,color: Colors.white),
                            onPressed: () {
                              setState(() {
                                age--;
                              });
                            },
                          ),
                          IconButton(
                            icon: Icon(Icons.add_circle_rounded,color: Colors.white),
                            onPressed: () {
                              setState(() {
                                age++;
                              });
                            },
                          ),
                        ],
                      ),
                    ],
                  ),
                ))
              ],
            ),
          ),
          SizedBox(height: 5,),
          InkWell(
            onTap: () {
              calculateBMI();
              Navigator.push(
                  context, MaterialPageRoute(builder: (context) => ms()));
            },
            child: Container(
              height: 60,
              width: 200,
              decoration: BoxDecoration(
                  color: Colors.pinkAccent,
                  borderRadius: BorderRadius.circular(10)),
              child: Column(
                mainAxisAlignment: MainAxisAlignment.center,
                crossAxisAlignment: CrossAxisAlignment.center,
                children: [
                  Text(
                    'calculate',
                    style: TextStyle(fontSize: 20),
                  ),
                ],
              ),
            ),
          ),
          SizedBox(height: 5,)
        ],
      ),
    );
  }
}
