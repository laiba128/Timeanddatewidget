# Timeanddatewidget

import 'package:flutter/material.dart';
import 'package:intl/intl.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      debugShowCheckedModeBanner: false,
      theme: ThemeData(
        primarySwatch: Colors.green,
      ),
      home: const MyHomePage(title: 'Flutter Demo'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  const MyHomePage({super.key, required this.title});

  final String title;

  @override
  State<MyHomePage> createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  DateTime? selectedDate; // To store selected date

  @override
  Widget build(BuildContext context) {
    var time = DateTime.now();
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.green,
        title: Text(widget.title), // Dynamically set the title
      ),
      body: Center(
        child: Container(

          child: SingleChildScrollView(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Text(
                  'CHECK CURRENT DATE AND TIME',
                  style: TextStyle(fontSize: 25, fontWeight: FontWeight.bold),
                ),
                Container(
                  height: 11,
                ),
                Text(
                  'Current time: ${DateFormat('jms').format(time)}',
                  style: TextStyle(fontSize: 25),
                ),
                Text(
                  'Current date: ${DateFormat('yMMMMd').format(time)}',
                  style: TextStyle(fontSize: 25),
                ),
                Container(
                  height: 11,
                ),
                ElevatedButton(
                  onPressed: () {
                    setState(() {
                      // This is for updating the new state
                    });
                  },
                  child: Text(
                    "Currentt",
                    style: TextStyle(fontSize: 25),
                  ),
                ),
                Container(
                  height: 17,
                ),
                Text(
                  "Select Date & Time",
                  style: TextStyle(fontSize: 26),
                ),

                Container(
                  height: 19,
                ),
                ElevatedButton(
                  onPressed: () async {
                    DateTime? datePicker = await showDatePicker(
                      context: context,
                      initialDate: DateTime.now(),
                      firstDate: DateTime(2021),
                      lastDate: DateTime(2025),
                    );
                    if (datePicker != null) {
                      print(" Date Selected :  ${datePicker.year}: ${datePicker.hour}: ${datePicker.day}");
                    }
                  },
                  child: Text(
                    "Select Date",
                    style: TextStyle(fontSize: 25),
                  ),
                ),
                ElevatedButton(
                  onPressed: () async {
                    TimeOfDay? TimePicker = await showTimePicker(
                      context: context,
                      initialTime: TimeOfDay.now(),
                      initialEntryMode: TimePickerEntryMode.input
                    );
                 if(TimePicker!=null){
                   print("Selected Time:  ${TimePicker.hour}: ${TimePicker.minute}");
                 }
                  },
                  child: Text(
                    "Select Time",
                    style: TextStyle(fontSize: 25),
                  ),
                ),
                // Display selected date after the date picker

              ],
            ),
          ),
        ),
      ),
    );
  }
}
