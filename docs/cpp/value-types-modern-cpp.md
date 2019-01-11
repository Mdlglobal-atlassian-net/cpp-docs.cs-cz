---
title: Typy hodnot (moderní verze jazyka C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
ms.openlocfilehash: 32cdb29ec1c59081ad7e0493888f290f21561d2b
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220345"
---
# <a name="value-types-modern-c"></a>Typy hodnot (moderní verze jazyka C++)

Třídy jazyka C++ jsou ve výchozích hodnotách. Toto téma obsahuje úvodní přehled typy hodnot a problémy týkající se jejich použití.

## <a name="value-vs-reference-types"></a>Hodnoty a odkazové typy

Jak už jsme uvedli, jsou třídy jazyka C++ ve výchozích hodnotách. Mohou být určeny jako typy odkazů, které povolit tak polymorfní chování pro podporu objektově orientované programování. Typy hodnot jsou někdy zobrazit z pohledu paměti a rozložení ovládacího prvku, že typy odkazů jsou o základních tříd a virtuálních funkcí pro polymorfní účely. Ve výchozím nastavení jsou typy hodnot kopírovatelné, což znamená, že je vždycky kopírovací konstruktor a operátor přiřazení kopie. Pro typy odkazů, provedete třídy kopírovatelná (zakažte konstruktor kopie a operátor přiřazení kopie) a použijte virtuální destruktor, který podporuje jejich zamýšlený polymorfismu. Typy hodnot jsou také o obsahu, které při jejich kopírování, vždy získáte dvě nezávislé hodnoty, které je možné upravit samostatně. Typy odkazů jsou o identitě - jaký druh objektu jde? Z tohoto důvodu "referenční typy" jsou také označovány jako "polymorfní typy".

Pokud chcete skutečně jako odkaz na typ (základní třída, virtuální funkce), je nutné explicitně zakázat kopírování, jak je znázorněno `MyRefType` třídy v následujícím kódu.

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

Kompilování výše uvedený kód způsobí následující chybu:

```Output
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'
        meow.cpp(5) : see declaration of 'MyRefType::operator ='
        meow.cpp(3) : see declaration of 'MyRefType'
```

## <a name="value-types-and-move-efficiency"></a>Typy hodnot a přesunout efektivity

Režijní náklady na kopírování přidělení je vyloučeno z důvodu optimalizace nové kopie. Například při vkládání řetězce uprostřed vektor řetězce, bude žádné kopírování přerozdělení režijní náklady, pouze move - i v případě, že výsledkem zvětšit vektoru samotný. To platí i pro jiné operace, například provádění operace přidat na dvě velmi velké objekty. Jak povolit tyto operace optimalizace hodnotu? V některé kompilátory C++ kompilátor umožní to pro vás implicitně, stejně jako kopírovací konstruktory mohou být automaticky generovaný kompilátorem. Ale v jazyce Visual C++, třídě muset "přihlásit" k přesunutí přiřazení a konstruktory jeho deklarací v definici třídy. Toho lze dosáhnout pomocí dvojitých ampersandu (& &) odkaz na rvalue v odpovídající člen funkce deklarace a definice konstruktor přesunutí a metody přiřazení přesunu.  Také je třeba vložit správný kód "odcizit vnitřností" ze zdrojového objektu.

Jak rozhodnout, pokud potřebujete přesunout povolené? Pokud již víte, že je že nutné zkopírovat konstrukce povolena, budete zřejmě chtít přesunout povoleno, zda může být levnější než hluboké kopírování. Ale pokud víte, že přesunete potřebovat podporu, ho neznamená nutně, že chcete, aby kopie povolené. Takovém případě by byla volána "jenom pro přesun typu". Příklad již ve standardní knihovně `unique_ptr`. Jako poznámka na okraj, starý `auto_ptr` je zastaralá a nahradila `unique_ptr` přesně vzhledem k absenci podporu sémantiky přesunutí v předchozí verzi jazyka C++.

Pomocí sémantiky přesunutí návratové hodnoty nebo můžete vložit ve středu. Přesunutí je optimalizace kopie. Je nutné pro přidělení haldy jako alternativní řešení. Vezměte v úvahu následujícím pseudokódu:

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

### <a name="enabling-move-for-appropriate-value-types"></a>Povolení přesunu pro typy odpovídající hodnotu

Pro třídu jako hodnota přesunutí kde může být levnější než hluboká kopie povolte konstrukci přesunu a přesunutí přiřazení efektivitu. Vezměte v úvahu následujícím pseudokódu:

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

Pokud povolíte konstrukce/přiřazení kopie, povolte konstrukce/přiřazení pro přesun také, pokud může být levnější než hluboké kopírování.

Některé *bez hodnoty* typy jsou jenom pro přesun, například když nemůžete klonovat prostředek pouze přenos vlastnictví. Příklad: `unique_ptr`.

## <a name="section"></a>Sekce

Obsah

## <a name="see-also"></a>Viz také:

[C++ – systém typů (moderní verze jazyka C++)](../cpp/cpp-type-system-modern-cpp.md)<br/>
[C++ vás vítá zpět (moderní verze jazyka C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
