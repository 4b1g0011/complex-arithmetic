//複數的類別定義
class Complex {
private:
    int re, im; //複數的實部與虛部
public:
    //建構子
    Complex(int r = 0, int i = 0) {
        re = r;
        im = i;
    }

    //加法運算子的重載
    Complex operator + (Complex const& obj) {
        Complex result;
        result.re = re + obj.re; //實部相加
        result.im = im + obj.im; //虛部相加
        return result;
    }

    //減法運算子的重載
    Complex operator - (Complex const& obj) {
        Complex result;
        result.re = re - obj.re; //實部相減
        result.im = im - obj.im; //虛部相減
        return result;
    }

    //乘法運算子的重載
    Complex operator * (Complex const& obj) {
        Complex result;
        result.re = re * obj.re - im * obj.im; //實部相乘減虛部相乘
        result.im = re * obj.im + im * obj.re; //實部相乘加虛部相乘
        return result;
    }

    //輸出複數的實部和虛部
    void display() {
        cout << re << " " << im << endl;
    }
};

int main()
{
    int n;
    Complex c[10]; //存放複數的陣列

    cin >> n; //讀入要處理的複數的組數
    for (int i = 0; i < n; i++) {
        char oper; //存放要進行的運算符號
        int ar, ai, br, bi; //存放兩個複數的實部和虛部
        cin >> oper >> ar >> ai >> br >> bi; //讀入運算符號和兩個複數的實部和虛部
        Complex a(ar, ai); //建立第一個複數
        Complex b(br, bi); //建立第二個複數

        switch (oper) { //根據運算符號進行相應的運算
        case '+':
            c[i] = a + b; //將運算結果存入陣列
            break;
        case '-':
            c[i] = a - b; //將運算結果存入陣列
            break;
        case '*':
            c[i] = a * b; //將運算結果存入陣列
            break;
        }
    }

    for (int i = 0; i < n; i++) { //輸出每個複數的結果
        c[i].display();
    }
}
