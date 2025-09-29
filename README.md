//1. FullLostPassword.cpp
#include <iostream>
#include <string>
#include <cctype>
using namespace std;

//Reverse
string FuncReverse (string word1){
    string R1;
    for (int i = word1.length()-1; i >=0; i--){
        R1 += word1[i];
    } return R1;
} 
//begone the vowel
bool Vowel (char vow){
    vow = tolower(vow);
    return vow == 'a' or vow == 'i' or vow =='u' or vow=='e' or vow=='o';
}
string BikinPass (string word){
    //ASCII code
    char HurufAwal = word [0];
    int AsciiHA = (int)HurufAwal;
    string AsciiHAS = to_string(AsciiHA);

    string NoVowel;
    for (char vow : word){
        if (!Vowel(vow)){
            NoVowel += vow;
        }
    }
    string pass = FuncReverse (NoVowel);

    int middle = pass.length()/2;
    string password = pass.substr(0,middle) + AsciiHAS + pass.substr(middle);
    return password;
    }

//Unscramble Pass
void Unscramble (string word){
    int posisi=-1;
    for (int i=0; i < word.length(); i++){
        if (isdigit(word[i])){
            posisi = i;
            break;
    }}

    if (posisi==-1){
        cout<<"invalid";
        return;
    }

    //take ascii and turn to str
    string Ascstr;
    while (posisi<word.length() and isdigit(word[posisi])){
        Ascstr += word[posisi];
        posisi++;
    }
    int asCode = stoi(Ascstr);

    string password = word.substr(0,word.find(Ascstr)) + word.substr(posisi);
    string passwordFix = FuncReverse (password);

    cout << passwordFix;
}
int main (){
    string input;
    string feedback;
    cout<<"Bikin katasandi atau unscramble?"<<endl;
    cin>>feedback;
    if (feedback == "katasandi"){
        cout << "Masukkan kata-kata untuk dirubah ke sandi : ";
        cin >> input;
        cout << BikinPass (input);}

    else if (feedback == "unscramble"){
        cout<<"Masukkan kata sandi yang kamu temui : "<<endl;
        cin>>input;
        Unscramble (input);
    }

    
    else {
        cout << "Salah, mohon masukkan 'katasandi' atau 'unscramble'";
    }

    return 0;
}

//2. TrafficLight.cpp
#include<iostream>
#include<string>
#include<cmath>
#include<vector>
//#include<cctype>
//#include<cstdlib>
using namespace std;

int main(){

    int time = 45, timeinput;
    string color1 = "yellow", color2 = "red", color3 = "green", finalColor;

    cout << "Waktu yang diinginkan: ";
    cin >> timeinput;

    if(timeinput>=45){
        for (int i = time; i <= timeinput; i++){ 
        
            for(int c = 1; c <= 3 && time <= timeinput; c++, time++){
                finalColor = color1;
            }
            
            for(int a = 1; a <= 80 && time <= timeinput; a++, time++){
                finalColor = color2;
            }

            for(int b = 1; b <= 20 && time <= timeinput; b++, time++){
                finalColor = color3;
            }

        }
    } else {
        cout << "Please input time greater than or equal to 45 seconds." << endl;
        return 0;
    }

    cout << "The color at time " << timeinput << " is " << finalColor;

    return 0;
}

