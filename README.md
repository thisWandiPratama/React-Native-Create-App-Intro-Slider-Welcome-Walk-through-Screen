# React-Native-Create-App-Intro-Slider-Welcome-Walk-through-Screen
React Native Create App Intro Slider Welcome Walk-through Screen | React Native Buat Aplikasi Intro Slider Welcome Walk-through Screen  | App Intro Slider is a group of multiple slides shows at the application start time in mobile phones. App Intro Slider contain useful information in picture format about application like what is the most useful nature of application. | App Intro Slider adalah sekelompok banyak slide yang ditampilkan pada waktu mulai aplikasi di ponsel. App Intro Slider berisi informasi bermanfaat dalam format gambar tentang aplikasi seperti apa sifat aplikasi yang paling berguna.

## Make a Project React Native Named "AppSlider" | Membuat sebuah Project React Native Bernama "AppSlider"
```
react-native init AppSlider
```
## Install react-native-app-intro-slider library.
```
npm install react-native-app-intro-slider --save
```
## Open your project’s App.js file and import ``StyleSheet``, ``View``, ``Text`` & ``Platform`` component | Buka File App.js Pada Proyek Anda dan Masukkan Komponen ``StyleSheet``, ``View``, ``Text`` & ``Platform``.
```
import React, { Component } from 'react';

import { StyleSheet, View, Text, Platform } from 'react-native';
```
## Import ``AppIntroSlider`` component from react-native-app-intro-slider library in your project | Masukkan Komponen ``AppIntroSlider`` dari libari react-native-app-intro-slider di proyek anda.
```
import AppIntroSlider from 'react-native-app-intro-slider';
```
Create ``constructor()`` in class. In constructor() we would make a State named as ``show_Main_App`` containing ``Boolean`` value. We would set its default value as false. This state is used to manage App intro slider and real application screen scenario. If state value is ``false`` then the App intro slider will display on screen and if its value is true then the application main screen will display.

Buat ``constructor()`` di class. Dalam ``constructor()`` kita akan membuat state bernama ``show_Main_App`` yang berisi nilai ``Boolean``. Kami akan menetapkan nilai default sebagai salah. Situasi ini digunakan untuk mengelola aplikasi slider intro dan skenario layar aplikasi yang sebenarnya. Jika nilainya ``salah``, slider intro aplikasi akan ditampilkan di layar dan jika nilainya benar, aplikasi yang diputar akan menampilkan.

```
 constructor(props){
    super(props);
    this.state={
      show_main_app:false
    }
  }
```
Create 2 functions named as ``on_Done_all_slides()`` and ``on_Skip_slides()``. In both functions we would change the state value from ``false`` to ``true``. We would call these functions ``on slider Done`` & ``Skip buttons``.


Buat 2 function bernama ``on_Done_all_slides()`` dan ``on_Skip_slides()``. Dalam kedua fungsi kami akan mengubah nilai status dari false menjadi true. Kami akan memanggil fungsi-fungsi(functions) ini pada tombol slider Selesai & Lewati.
```
on_Done_all_slides = () => {
    this.setState({ show_Main_App: true });
  };
 
  on_Skip_slides = () => {
    this.setState({ show_Main_App: true });
  };
```

Put a ``IF condition`` with ``show_Main_App state`` in render’s block. If the state value is ``true`` then it will show us the main application screen and if the state value is ``false`` then it will display the App intro slider screen. In the Else part we would create the ``AppIntroSlider`` component and call the both functions on ``onDone`` & ``onSkip`` prop.

Masukkan ``kondisi IF`` dengan status ``show_Main_App`` di blok render. Jika nilai state ``true`` maka akan menampilkan layar aplikasi utama dan jika nilai state ``false`` maka akan menampilkan layar slider intro App. Di bagian Lain kita akan membuat komponen ``AppIntroSlider`` dan memanggil kedua ``functions`` di ``onDone`` & ``onSkip`` prop.

slides : Here we calls the slides constant array created after styles.
slide: Di sini kita memanggil array konstan slide yang dibuat setelah gaya
```
render() {
    if (this.state.show_Main_App) {
      return (
        <View style={styles.MainContainer}>

          <Text style={{ textAlign: 'center', fontSize: 20, color: '#000' }}>

            This is your main App screen After App Intro.

          </Text>

        </View>
      );
    } else {
      return (
        <AppIntroSlider
          slides={slides}
          onDone={this.on_Done_all_slides}
          showSkipButton={true}
          onSkip={this.on_Skip_slides}
        />
      );
    }
  }
```
Creating Style.
```
const styles = StyleSheet.create({

  MainContainer: {
    flex: 1,
    paddingTop: (Platform.OS) === 'ios' ? 20 : 0,
    alignItems: 'center',
    justifyContent: 'center',
    padding: 20
  },
  title: {
    fontSize: 26,
    color: '#fff',
    fontWeight: 'bold',
    textAlign: 'center',
    marginTop: 20,
  },
  text: {
    color: '#fff',
    fontSize: 20,
  },
  image: {
    width: 200,
    height: 200,
    resizeMode: 'contain'
  }
});
```
Creating a constant array named as ``slides``. This array will contain all information about slides. We have to create the array at the end of code after declaring Style sheet code. because if we create the array before declaring style sheet code then the styles will not not be able to call successfully in slides.

Membuat array konstan bernama ``slides``. Array ini akan berisi semua informasi tentang slide. Kita harus membuat array di akhir kode setelah mendeklarasikan kode style sheet. karena jika kita membuat array sebelum mendeklarasikan kode style sheet maka style tidak akan berhasil memanggil dalam slide.
- key : Should be unique for each slide.
- title : Title of slide.
- text : Description text of slide.
- image : Pass the image Path in slide here.
- titleStyle : Call the title style here.
- textStyle : Description text style.
- imageStyle : Call the image style.
- backgroundColor : Define background color HEX color code format.

```
const slides = [
  {
    key: 'k1',
    title: 'Event Organizer',
    text: 'Best Event Organizers',
    image: {
      uri:
        'https://reactnativecode.com/wp-content/uploads/2019/04/calendar.png',
    },
    titleStyle: styles.title,
    textStyle: styles.text,
    imageStyle: styles.image,
    backgroundColor: '#FF1744',
  },
  {
    key: 'k2',
    title: 'Weather Reports',
    text: 'Latest Weather Reports',
    image: {
      uri:
        'https://reactnativecode.com/wp-content/uploads/2019/04/cloud.png',
    },
    titleStyle: styles.title,
    textStyle: styles.text,
    imageStyle: styles.image,
    backgroundColor: '#D500F9',
  },
  {
    key: 'k3',
    title: 'Technology Informations',
    text: 'Latest Technology Reports',
    image: {
      uri: 'https://reactnativecode.com/wp-content/uploads/2019/04/computer.png',
    },
    titleStyle: styles.title,
    textStyle: styles.text,
    imageStyle: styles.image,
    backgroundColor: '#2979FF',
  },
  {
    key: 'k4',
    title: 'Flight Bookings',
    text: ' Best Deals on Flights',
    image: {
      uri: 'https://reactnativecode.com/wp-content/uploads/2019/04/flight.png',
    },
    titleStyle: styles.title,
    textStyle: styles.text,
    imageStyle: styles.image,
    backgroundColor: '#1DE9B6',
  },
  {
    key: 'k5',
    title: 'Restaurant Bookings',
    text: ' 20% off on first Restaurant booking',
    image: {
      uri:
        'https://reactnativecode.com/wp-content/uploads/2019/04/restaurants.png',
    },
    titleStyle: styles.title,
    textStyle: styles.text,
    imageStyle: styles.image,
    backgroundColor: '#FF3D00',
  },
];
```

### Complete source code for App.js file class.
```
import React, { Component } from 'react';

import { StyleSheet, View, Text, Platform } from 'react-native';

import AppIntroSlider from 'react-native-app-intro-slider';

export default class App extends Component {

  constructor(props) {
    super(props);
    this.state = {

      show_Main_App: false

    };
  }

  on_Done_all_slides = () => {
    this.setState({ show_Main_App: true });
  };

  on_Skip_slides = () => {
    this.setState({ show_Main_App: true });
  };
  render() {
    if (this.state.show_Main_App) {
      return (
        <View style={styles.MainContainer}>

          <Text style={{ textAlign: 'center', fontSize: 20, color: '#000' }}>

            This is your main App screen After App Intro.

          </Text>

        </View>
      );
    } else {
      return (
        <AppIntroSlider
          slides={slides}
          onDone={this.on_Done_all_slides}
          showSkipButton={true}
          onSkip={this.on_Skip_slides}
        />
      );
    }
  }
}
const styles = StyleSheet.create({

  MainContainer: {
    flex: 1,
    paddingTop: (Platform.OS) === 'ios' ? 20 : 0,
    alignItems: 'center',
    justifyContent: 'center',
    padding: 20
  },
  title: {
    fontSize: 26,
    color: '#fff',
    fontWeight: 'bold',
    textAlign: 'center',
    marginTop: 20,
  },
  text: {
    color: '#fff',
    fontSize: 20,
  },
  image: {
    width: 200,
    height: 200,
    resizeMode: 'contain'
  }
});

const slides = [
  {
    key: 'k1',
    title: 'Event Organizer',
    text: 'Best Event Organizers',
    image: {
      uri:
        'https://reactnativecode.com/wp-content/uploads/2019/04/calendar.png',
    },
    titleStyle: styles.title,
    textStyle: styles.text,
    imageStyle: styles.image,
    backgroundColor: '#FF1744',
  },
  {
    key: 'k2',
    title: 'Weather Reports',
    text: 'Latest Weather Reports',
    image: {
      uri:
        'https://reactnativecode.com/wp-content/uploads/2019/04/cloud.png',
    },
    titleStyle: styles.title,
    textStyle: styles.text,
    imageStyle: styles.image,
    backgroundColor: '#D500F9',
  },
  {
    key: 'k3',
    title: 'Technology Informations',
    text: 'Latest Technology Reports',
    image: {
      uri: 'https://reactnativecode.com/wp-content/uploads/2019/04/computer.png',
    },
    titleStyle: styles.title,
    textStyle: styles.text,
    imageStyle: styles.image,
    backgroundColor: '#2979FF',
  },
  {
    key: 'k4',
    title: 'Flight Bookings',
    text: ' Best Deals on Flights',
    image: {
      uri: 'https://reactnativecode.com/wp-content/uploads/2019/04/flight.png',
    },
    titleStyle: styles.title,
    textStyle: styles.text,
    imageStyle: styles.image,
    backgroundColor: '#1DE9B6',
  },
  {
    key: 'k5',
    title: 'Restaurant Bookings',
    text: ' 20% off on first Restaurant booking',
    image: {
      uri:
        'https://reactnativecode.com/wp-content/uploads/2019/04/restaurants.png',
    },
    titleStyle: styles.title,
    textStyle: styles.text,
    imageStyle: styles.image,
    backgroundColor: '#FF3D00',
  },
];
```