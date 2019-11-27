---
title: Třídy jazyka C++ jako typy hodnot
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
ms.openlocfilehash: 1aabcad46e848e1a499a142adaba5002a829bbf5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246023"
---
# <a name="c-classes-as-value-types"></a>Třídy jazyka C++ jako typy hodnot

C++třídy jsou ve výchozím typu hodnot. Mohou být zadány jako typy odkazů, které umožňují polymorfní chování pro podporu objektově orientovaného programování. Typy hodnot se někdy zobrazují z perspektivy ovládacího prvku paměť a rozložení, zatímco typy odkazů se týkají základních tříd a virtuálních funkcí pro polymorfní účely. Ve výchozím nastavení jsou typy hodnot zkopírovány, což znamená, že je vždy kopírovací konstruktor a operátor přiřazení kopie. U typů odkazů uděláte nekopírovatelné třídy (zakažte kopírovací konstruktor a operátor přiřazení kopie) a použijte virtuální destruktor, který podporuje jejich zamýšlené polymorfismus. Typy hodnot jsou také informace o obsahu, který při jejich kopírování vždy poskytují dvě nezávislé hodnoty, které lze změnit samostatně. Typy odkazů jsou o identitě – jaký druh objektu je? Z tohoto důvodu jsou "odkazy na typy" označovány také jako "polymorfní typy".

Pokud skutečně chcete typ odkazu (základní třída, virtuální funkce), je nutné explicitně zakázat kopírování, jak je znázorněno ve třídě `MyRefType` v následujícím kódu.

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

Kompilace výše uvedeného kódu způsobí následující chybu:

```Output
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'
        meow.cpp(5) : see declaration of 'MyRefType::operator ='
        meow.cpp(3) : see declaration of 'MyRefType'
```

## <a name="value-types-and-move-efficiency"></a>Typy hodnot a efektivita přesunu

Kvůli nové optimalizaci kopírování se vyhnete režijním nákladům na přidělení. Například při vložení řetězce do středu vektoru řetězce nebude provedena žádná režie beze opětovného přidělení kopírování, a to i v případě, že výsledkem bude zvětšení samotného vektoru. To platí i pro jiné operace, například při provádění operace přidání na dvou velmi velkých objektech. Jak povolíte tyto optimalizace operací s hodnotami? V některých C++ kompilátorech vám kompilátor tuto možnost umožní implicitně, podobně jako kopírovací konstruktory mohou být automaticky generovány kompilátorem. V aplikaci C++však bude vaše třída muset "vyjádřit", aby přesunula přiřazení a konstruktory tím, že je deklaruje v definici vaší třídy. K tomu je potřeba použít odkaz na rvalue typu Double ampersand (& &) v příslušných deklaracích členské funkce a definování konstruktoru přesunutí a metody přiřazení přesunutí.  Musíte také vložit správný kód do části "ukrást Guts" ze zdrojového objektu.

Jak se rozhodnout, jestli potřebujete přesun povolit? Pokud už víte, že potřebujete konstrukci kopírování povolit, budete pravděpodobně chtít přesunout povolený, pokud může být levnější než hluboká kopie. Pokud ale víte, že potřebujete podporu přesunout, neznamená to nutně, že chcete povolit kopírování. Tento druhý případ se nazývá "typ pouze pro přesun". Příklad, který je již ve standardní knihovně, je `unique_ptr`. Jako Poznámka na straně typu se stará `auto_ptr` zastaralá a byla nahrazena `unique_ptr`ou v důsledku nedostatku podpory sémantiky přesunutí v předchozí verzi nástroje C++.

Když použijete možnost přesunout sémantiku, můžete vracet hodnoty za běhu nebo vložením do středu. Přesunutí je optimalizace kopírování. Jako alternativní řešení je potřeba přidělení haldy. Vezměte v úvahu následující pseudokódu:

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

### <a name="enabling-move-for-appropriate-value-types"></a>Povolení přesunutí pro příslušné typy hodnot

Pro třídu podobnou hodnotě, kde může být přesunutí levnější než hluboká kopie, povolte přesunutí konstrukce a přesunutí přiřazení pro efektivitu. Vezměte v úvahu následující pseudokódu:

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

Pokud povolíte vytváření a přiřazování kopírování, povolte také možnost přesunout stavbu/přiřazení, pokud může být levnější než hluboká kopie.

Některé typy *bez hodnot* jsou pouze pro přesun, například když nelze klonovat prostředek, převeďte pouze vlastnictví. Příklad: `unique_ptr`.

## <a name="see-also"></a>Viz také:

[C++systém typů](../cpp/cpp-type-system-modern-cpp.md)<br/>
[Vítejte zpět naC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
