#include <iostream>
#include <string>
#include <fstream>
#include <vector>
#include <iomanip>
#include <algorithm>
using namespace std;

class ParttimeWorkers {
    
    protected:
       string name;
       int OKtime;
    public:
       void setName(string newName);
       void setOKtime(int newOKtime);//0:9時から１２時 1:12時から17時　2:17時から22時　働ける時間
       void show();
};

class TKG : public ParttimeWorkers {
    private:
       string day;
    public:
       void setDay (string newDay);
       void show1();
       void show2();
       void show3();
};

void ParttimeWorkers::setName(string newName) {
    name  = newName;
}

void ParttimeWorkers::setOKtime(int newOKtime) {
    OKtime = newOKtime;
}

void ParttimeWorkers::show() {
    cout << "名前:" << name <<  "\t 働ける時間：" << OKtime << endl;
}

void TKG::setDay(string newDay) {
    day = newDay;
}

void TKG::show1() {
    cout << "名前：" << name << "\t 働ける時間：" << left << setw(6) << OKtime << "\t働ける曜日："  << day << endl;
}

void TKG::show2() {
    cout <<  "名前：" << name << "\t 働ける時間：" << OKtime << endl;
}

void TKG::show3() {
    cout << "名前：" << name << "\t 働ける曜日：" << day << endl;
}

int main() {
    vector<TKG> syukkinkanoubi;
    
    ifstream infile("File1");
    
    int OKtime;
    string name, day;
    while (infile >> name >> OKtime >> day) {
        syukkinkanoubi.emplace_back();
        syukkinkanoubi[syukkinkanoubi.size() - 1].setName(name);
        syukkinkanoubi[syukkinkanoubi.size() - 1].setOKtime(OKtime);
        syukkinkanoubi[syukkinkanoubi.size() - 1].setDay(day);
    }
    infile.close();
    
    cout << "働ける時間　0:9時から12時　1:12時から17時　2:17時から22時\n" << endl;
    for (int i = 0; i < syukkinkanoubi.size(); ++i) 
    //show1は名前・働ける時間・働ける曜日　
    //show2は名前・働ける時間
    //show3は名前・働ける曜日
    syukkinkanoubi[i].show1();
}
