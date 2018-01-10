---
title: "Uniform inicializace a delegování konstruktorů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: aa4daa64-eaec-4a3c-ade4-d9325e31e9d4
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 68d8f9724ba7f26ac9df9b81c1e4c3f6213f76a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="uniform-initialization-and-delegating-constructors"></a>Jednotná inicializace a delegování konstruktorů
V moderní verze jazyka C++, můžete použít *složených závorek inicializace* pro jakýkoli typ bez symbolem rovná se. Navíc můžete delegování konstruktorů zjednodušit kód, když máte více konstruktory, které provádějí podobné práci.  
  
## <a name="brace-initialization"></a>Inicializace závorek  
 Inicializace závorek můžete použít u třída, struktura nebo union. Pokud typ má výchozí konstruktor, implicitně nebo explicitně deklarovat, můžete použít výchozí inicializace závorek (s prázdnou složené závorky). Například může pomocí výchozí i jiné než výchozí závorek inicializace inicializovat následující třídy:  
  
```cpp  
#include <string>  
using namespace std;  
  
class class_a {  
public:  
    class_a() {}  
    class_a(string str) : m_string{ str } {}  
    class_a(string str, double dbl) : m_string{ str }, m_double{ dbl } {}  
double m_double;  
string m_string;  
};  
  
int main()  
{  
    class_a c1{};  
    class_a c1_1;  
  
    class_a c2{ "ww" };  
    class_a c2_1("xx");  
  
    // order of parameters is the same as the constructor  
    class_a c3{ "yy", 4.4 };  
    class_a c3_1("zz", 5.5);  
}  
  
```  
  
 Pokud třída má jiné než výchozí konstruktory, je pořadí, ve které třídy členy zobrazí ve složené závorce inicializátoru pořadí, ve kterém příslušné parametry zobrazí v konstruktoru, není pořadí, ve které jsou deklarované členy (stejně jako u `class_a` v předchozí příklad). Jinak hodnota pokud typ nemá žádný konstruktor deklarované, pořadí členů zobrazených v inicializátoru závorek je stejný jako pořadí, ve které jsou deklarovány; v takovém případě můžete inicializovat jako řadu veřejné členy jak chcete, ale nedá přeskočit kteréhokoli člena. Následující příklad ukazuje pořadí, ve kterém se používá ve složené závorce inicializace, pokud neexistuje žádný deklarované konstruktor:  
  
```cpp  
class class_d {  
public:  
    float m_float;  
    string m_string;  
    wchar_t m_char;  
};  
  
int main()  
{  
    class_d d1{};  
    class_d d1{ 4.5 };  
    class_d d2{ 4.5, "string" };  
    class_d d3{ 4.5, "string", 'c' };  
  
    class_d d4{ "string", 'c' }; // compiler error  
    class_d d5("string", 'c', 2.0 }; // compiler error  
}   
```  
  
 Pokud výchozí konstruktor je explicitně deklarován ale označena k odstranění, nebude možné použít výchozí složené závorce inicializace:  
  
```cpp  
class class_f {  
public:  
    class_f() = delete;  
    class_f(string x): m_string { x } {}  
    string m_string;  
};  
int main()  
{  
    class_f cf{ "hello" };  
    class_f cf1{}; // compiler error C2280: attempting to reference a deleted function  
}  
```  
  
 Můžete použít složené závorce inicializace kdekoli by obvykle provádí inicializace – například jako parametr funkce nebo vrací hodnotu, nebo pomocí `new` – klíčové slovo:  
  
```cpp  
class_d* cf = new class_d{4.5};  
kr->add_d({ 4.5 });  
return { 4.5 };  
  
```  
  
## <a name="initializerlist-constructors"></a>initializer_list konstruktory  
 [Initializer_list třída](../standard-library/initializer-list-class.md) reprezentuje seznam objektů zadaného typu, který lze použít v konstruktoru a v jiném kontextu. Initializer_list můžete vytvořit pomocí závorek inicializace:  
  
```cpp  
initializer_list<int> int_list{5, 6, 7};  
```  
  
> [!IMPORTANT]
>  Pokud chcete používat tuto třídu, musí obsahovat [< initializer_list >](../standard-library/initializer-list.md) záhlaví.  
  
 `initializer_list` Lze zkopírovat. V tomto případě členů nového seznamu jsou odkazy na členy původního seznamu:  
  
```cpp  
initializer_list<int> ilist1{ 5, 6, 7 };  
initializer_list<int> ilist2( ilist1 );  
if (ilist1.begin() == ilist2.begin())  
    cout << "yes" << endl; // expect "yes"  
  
```  
  
 Třídy kontejnerů standardní knihovny a také `string`, `wstring`, a `regex`, mají `initializer_list` konstruktory. Následující příklady ukazují, jak do složených závorek inicializace pomocí těchto konstruktorů:  
  
```cpp  
vector<int> v1{ 9, 10, 11 };   
map<int, string> m1{ {1, "a"}, {2, "b"} };  
string s{ 'a', 'b', 'c' };   
regex rgx{'x', 'y', 'z'};   
```  
  
## <a name="delegating-constructors"></a>Delegování konstruktorů  
 Mnoho třídy mají více konstruktory, které provádějí podobné věci – například ověření parametrů:  
  
```cpp  
class class_c {  
public:  
    int max;  
    int min;  
    int middle;  
  
    class_c() {}  
    class_c(int my_max) {   
        max = my_max > 0 ? my_max : 10;   
    }  
    class_c(int my_max, int my_min) {   
        max = my_max > 0 ? my_max : 10;  
        min = my_min > 0 && my_min < max ? my_min : 1;  
    }  
    class_c(int my_max, int my_min, int my_middle) {  
        max = my_max > 0 ? my_max : 10;  
        min = my_min > 0 && my_min < max ? my_min : 1;  
        middle = my_middle < max && my_middle > min ? my_middle : 5;  
    }  
};  
```  
  
 Kód opakující se může snížit tak, že přidáte funkci, která nepodporuje všechny ověření, ale kód pro `class_c` bude možné snadněji pochopit a spravovat, pokud jeden konstruktor může delegovat některé práce na jiný. Chcete-li přidat delegování konstruktorů, použijte `constructor (. . .) : constructor (. . .)` syntaxe:  
  
```cpp  
class class_c {  
public:  
    int max;  
    int min;  
    int middle;  
  
    class_c(int my_max) {   
        max = my_max > 0 ? my_max : 10;   
    }  
    class_c(int my_max, int my_min) : class_c(my_max) {   
        min = my_min > 0 && my_min < max ? my_min : 1;  
    }  
    class_c(int my_max, int my_min, int my_middle) : class_c (my_max, my_min){  
        middle = my_middle < max && my_middle > min ? my_middle : 5;  
}  
};  
int main() {  
  
    class_c c1{ 1, 3, 2 };  
}  
  
```  
  
 Krocích předchozí příklad, Všimněte si, že konstruktoru `class_c(int, int, int)` nejprve volá konstruktor `class_c(int, int)`, který volá `class_c(int)`. Každá z konstruktorů provádí pouze práci, kterou není provádí další konstruktory.  
  
 První konstruktor, který se nazývá inicializuje objekt tak, aby všichni její členové jsou inicializovány v daném okamžiku. Inicializace členů v konstruktoru, která deleguje jiné konstruktoru, nelze provést, jak je vidět tady:  
  
```cpp  
class class_a {  
public:  
    class_a() {}  
    // member initialization here, no delegate  
    class_a(string str) : m_string{ str } {}  
  
    //can’t do member initialization here  
    // error C3511: a call to a delegating constructor shall be the only member-initializer  
    class_a(string str, double dbl) : class_a(str) , m_double{ dbl } {}  
  
    // only member assignment  
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }  
    double m_double{ 1.0 };  
    string m_string;  
};  
  
```  
  
 Další příklad ukazuje použití dat člena nestatické inicializátory. Všimněte si, že pokud konstruktor inicializuje také členem daného data, je přepsat inicializátoru člen:  
  
```cpp  
class class_a {  
public:  
    class_a() {}  
    class_a(string str) : m_string{ str } {}  
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }  
    double m_double{ 1.0 };  
    string m_string{ m_double < 10.0 ? "alpha" : "beta" };  
};  
  
int main() {  
    class_a a{ "hello", 2.0 };  //expect a.m_double == 2.0, a.m_string == "hello"  
    int y = 4;  
}  
```  
  
 Syntaxe delegování konstruktor nezabrání vytvoření náhodného konstruktor rekurze – Constructor1 volá Constructor2, který volá Constructor1 – a žádné chyby jsou vyvolány, dokud nedojde k přetečení zásobníku. Je vaší povinností vyhnout cyklům.  
  
```cpp  
class class_f{  
public:  
    int max;  
    int min;  
  
    // don't do this  
    class_f() : class_f(6, 3){ }  
    class_f(int my_max, int my_min) : class_f() { }  
};  
```