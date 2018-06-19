---
title: Hodnota typů (moderní verze jazyka C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7e49c97bca86b8d2debde2f5b132f7dde16998e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423415"
---
# <a name="value-types-modern-c"></a>Typy hodnot (moderní verze jazyka C++)
Třídy C++ jsou typy výchozí hodnotu. Toto téma obsahuje úvodní přehled typů hodnot a otázky týkající se jejich použití.  
  
## <a name="value-vs-reference-types"></a>Hodnota oproti odkazové typy  
 Jako dříve jsme si říkali, C++ třídy jsou typy výchozí hodnotu. Může být zadaný jako odkazové typy, které umožňují polymorfní chování pro podporu objektově orientované programování. Typy hodnot se někdy zobrazit z pohledu paměti a rozložení ovládacího prvku, zatímco odkazové typy jsou o základní třídy a virtuální funkce polymorfní důvodů. Ve výchozím nastavení jsou typy hodnot kopírovatelná, což znamená, že je vždy kopírovacího konstruktoru a operátor přiřazení kopírování. U typů odkazu provedete třída bez kopírovatelná (zakázat kopírovacího konstruktoru a operátor přiřazení kopie) a používat virtuální destruktor, která podporuje jejich zamýšlený polymorfismus. Typy hodnot jsou také o obsahu, které při kopírování, vždy získáte dvě nezávislé hodnoty, které je možné upravit samostatně. Odkazové typy jsou o identitě - jaký druh objektu je? Z tohoto důvodu "odkazové typy" jsou také označovány jako "polymorfní typy".  
  
 Pokud chcete skutečně typu odkaz jako (základní třída, virtuální funkce), je nutné explicitně zakázat kopírování, jak je znázorněno `MyRefType` třídy v následujícím kódu.  
  
```cpp  
// cl /EHsc /nologo /W4  
  
class MyRefType {  
private:  
    MyRefType & operator=(const MyRefType &);  
    MyRefType(const MyRefType &);  
public:  
    MyRefType () {}  
};  
  
int main()  
{  
    MyRefType Data1, Data2;  
    // ...  
    Data1 = Data2;  
}  
```  
  
 Kompilování výše uvedený kód bude mít za následek k následující chybě:  
  
```Output  
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'  
        meow.cpp(5) : see declaration of 'MyRefType::operator ='  
        meow.cpp(3) : see declaration of 'MyRefType'  
  
```  
  
## <a name="value-types-and-move-efficiency"></a>Typů hodnot a přesunout efektivita  
 Z důvodu optimalizace nové kopie je vyhnout kopírování přidělení režii. Například když vložíte řetězec uprostřed vektoru řetězců, budou existovat žádné kopie nové přidělení režijní náklady, jenom move - i v případě, že výsledkem je to zvětšit vektoru sám sebe. To platí také pro jiné operace, například při provádění operace přidat v dva velké objekty. Jak můžete tyto operace optimalizace hodnota povolit? V některých kompilátory C++ kompilátor vám umožní to pro vás implicitně, jako kopie konstruktorů můžete automaticky generované kompilátorem. V jazyce Visual C++, však třídě nutné "opt-in" přesunout přiřazení a konstruktory deklarací ve vaší definice třídy. To se dá udělat pomocí dvojité ampersand (& &) deklarátor odkazu hodnoty v příslušného člena funkce deklarace a definující konstruktor move a přesuňte přiřazení metody.  Také je třeba vložit správný kód ke "krádeži vnitřností" mimo zdrojový objekt.  
  
 Jak můžete rozhodnout, pokud je třeba přesunout, povolené? Pokud už víte, že zkopírujete potřebovat konstrukce povoleno, budete ho zřejmě chtít přesunout povoleno, zda může být levnějších než hloubkové kopie. Ale pokud víte, že je třeba přesunout podpory, ho není nutně znamenat, že chcete, aby kopie povolené. Takovém případě by být volána "pouze přesunutí typ". Je například již v knihovně standardní `unique_ptr`. Jako poznámky na okraj starý `auto_ptr` je zastaralá a nahradila `unique_ptr` přesněji z důvodu nedostatku přesunutí sémantiku podpory v předchozí verzi C++.  
  
 Pomocí sémantiky přesunutí můžete vrátit hodnotu nebo insert-in-middle. Přesunutí je optimalizace kopie. Je nutné pro přidělení haldy jako alternativní řešení. Vezměte v úvahu následující pseudokódu:  
  
```cpp  
#include <set>  
#include <vector>  
#include <string>  
using namespace std;  
  
//...  
set<widget> LoadHugeData() {  
    set<widget> ret;  
    // ... load data from disk and populate ret  
    return ret;  
}  
//...  
widgets = LoadHugeData();   // efficient, no deep copy  
  
vector<string> v = IfIHadAMillionStrings();  
v.insert( begin(v)+v.size()/2, "scott" );   // efficient, no deep copy-shuffle  
v.insert( begin(v)+v.size()/2, "Andrei" );  // (just 1M ptr/len assignments)  
//...  
HugeMatrix operator+(const HugeMatrix& , const HugeMatrix& );  
HugeMatrix operator+(const HugeMatrix& ,       HugeMatrix&&);  
HugeMatrix operator+(      HugeMatrix&&, const HugeMatrix& );  
HugeMatrix operator+(      HugeMatrix&&,       HugeMatrix&&);  
//...  
hm5 = hm1+hm2+hm3+hm4+hm5;   // efficient, no extra copies  
```  
  
### <a name="enabling-move-for-appropriate-value-types"></a>Povolení přesunutí pro typy odpovídající hodnotu  
 Pro třídu jako hodnota, kde lze přesunout levnějších než kopii hloubkové povolit vytváření přesunutí a přesuňte přiřazení pro efektivitu. Vezměte v úvahu následující pseudokódu:  
  
```cpp  
#include <memory>  
#include <stdexcept>  
using namespace std;  
// ...  
class my_class {  
    unique_ptr<BigHugeData> data;  
public:  
    my_class( my_class&& other )   // move construction  
        : data( move( other.data ) ) { }  
    my_class& operator=( my_class&& other )   // move assignment  
    { data = move( other.data ); return *this; }  
    // ...  
    void method() {   // check (if appropriate)  
        if( !data )   
            throw std::runtime_error("RUNTIME ERROR: Insufficient resources!");  
    }  
};  
  
```  
  
 Pokud povolíte kopírování konstrukce nebo přiřazení, také povolte přesunutí konstrukce nebo přiřazení, zda může být levnějších než hloubkové kopie.  
  
 Některé *bez hodnoty* typy jsou přesunout jen, například když nelze klonovat prostředku, pouze přenos vlastnictví. Příklad: `unique_ptr`.  
  
## <a name="section"></a>Část  
 Obsah  
  
## <a name="see-also"></a>Viz také  
 [C++ – systém typů](../cpp/cpp-type-system-modern-cpp.md)   
 [C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)