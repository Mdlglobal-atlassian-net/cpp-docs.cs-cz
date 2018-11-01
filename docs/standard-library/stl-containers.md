---
title: Kontejnery standardní knihovny C++
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, template class containers
- containers, C++ Standard Library
ms.assetid: 8e915ca1-19ba-4f0d-93c8-e2c3bfd638eb
ms.openlocfilehash: 240a05822ea93493c917469fc18fa8a9c224359d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568620"
---
# <a name="c-standard-library-containers"></a>Kontejnery standardní knihovny C++

Standardní knihovna poskytuje různé zajišťující bezpečnost typů kontejnery pro ukládání kolekcí souvisejících objektů. Kontejnery jsou třídy šablony. Pokud deklarujete proměnnou kontejneru, zadejte typ prvků, které bude obsahovat kontejneru. Kontejnery lze zkonstruovat se seznamy inicializátorů. Mají členské funkce pro přidání a odebrání prvků a provádění dalších operací.

Iterovat přes prvky v kontejneru a přístup k jednotlivým prvkům pomocí [iterátory](../standard-library/iterators.md). Pomocí jejich členské funkce a operátory stejně jako globální funkce lze explicitně použití iterátorů. Můžete použít také je implicitně, třeba v rozsahu-smyčky for. Iterátory pro všechny kontejnery standardní knihovny C++, které mají společné rozhraní, ale každý kontejner definuje vlastní specializované iterátory.

Kontejnery lze rozdělit do tří kategorií: pořadí kontejnery, asociativní kontejnery a adaptéry kontejneru.

## <a name="sequence_containers"></a> Kontejnery sekvence

Kontejnery sekvence si zachovávají řazení vložených prvků, že zadáte.

A `vector` kontejneru se chová jako pole, ale může automaticky růst podle potřeby. Je náhodný přístup a ukládán souvisle a délka je vysoce flexibilní. Z těchto důvodů a další věci `vector` je kontejner upřednostňovaným pořadím pro většinu aplikací. Pokud máte pochybnosti o jaký druh pořadí kontejner, aby používal, spusťte s použitím vektoru! Další informace najdete v tématu [vector – třída](../standard-library/vector-class.md).

`array` Kontejner obsahuje některé síly `vector`, ale délka není tak pružná. Další informace najdete v tématu [array – třída](../standard-library/array-class-stl.md).

A `deque` kontejneru (fronta se dvěma konci) umožňuje rychlé vložení a odstranění na začátku a konci kontejneru. Sdílí náhodný přístup a flexibilní délky výhody `vector`, ale není souvislé. Další informace najdete v tématu [třídou deque](../standard-library/deque-class.md).

A `list` kontejneru je dvakrát propojený seznam, který umožňuje obousměrný přístup, rychlé vkládání a odstranění kdekoli v kontejneru, ale neumožňuje náhodný přístup prvku v kontejneru. Další informace najdete v tématu [list – třída](../standard-library/list-class.md).

A `forward_list` kontejneru je jednotlivě propojený seznam – verze dopředný přístup `list`. Další informace najdete v tématu [forward_list – třída](../standard-library/forward-list-class.md).

## <a name="associative-containers"></a>Asociativní kontejnery

V asociativních kontejnerech jsou prvky vloženy v předem definovaném pořadí, například seřazeny vzestupně. Neuspořádané asociativní kontejnery jsou také k dispozici. Asociativní kontejnery lze rozdělit do dvou podskupin: mapy a sady.

A `map`, někdy označuje jako slovník, se skládá z dvojice klíč/hodnota. Klíč slouží k uspořádání pořadí a hodnota je přidružená tomuto klíči. Například `map` může obsahovat klíče, které reprezentují všechna jedinečná slova v textu a odpovídající hodnoty, které představují počet případů, kdy se každé slovo zobrazí v textu. Neuspořádaná verze `map` je `unordered_map`. Další informace najdete v tématu [map – třída](../standard-library/map-class.md) a [unordered_map – třída](../standard-library/unordered-map-class.md).

A `set` je pouze vzestupný kontejner jedinečných prvků, hodnota je také klíč. Neuspořádaná verze `set` je `unordered_set`. Další informace najdete v tématu [nastavit třídy](../standard-library/set-class.md) a [unordered_set – třída](../standard-library/unordered-set-class.md).

Obě `map` a `set` Povolit jenom jednu instanci klíče nebo prvek, který má být vložen do kontejneru. Pokud je požadováno více instancí prvků, použijte `multimap` nebo `multiset`. Neseřazené verze jsou `unordered_multimap` a `unordered_multiset`. Další informace najdete v tématu [multimap – třída](../standard-library/multimap-class.md), [unordered_multimap – třída](../standard-library/unordered-multimap-class.md), [multiset – třída](../standard-library/multiset-class.md), a [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).

Uspořádané mapy a sady podporují obousměrné iterátory a jejich neuspořádané protějšky podporují u dopředné iterátory. Další informace najdete v tématu [iterátory](../standard-library/iterators.md).

### <a name="heterogeneous-lookup-in-associative-containers-c14"></a>Heterogenní vyhledávání v asociativních kontejnerech (C ++ 14)

Uspořádané asociativní kontejnery (mapování, multimap, sada a multiset) nyní heterogenní podpora vyhledávání, což znamená, že už nebude potřeba předat přesně stejný typ objektu jako klíče nebo prvek v členské funkce, jako `find()` a `lower_bound()` . Místo toho můžete předat libovolný typ, pro kterou přetížený `operator<` je definován, která umožňuje porovnání pro typ klíče.

Na základě přihlášení je povoleno heterogenní vyhledávání, když zadáte `std::less<>` nebo `std::greater<>` "diamond funktor" Komparátor při deklarování proměnné kontejneru, jak je znázorněno zde:

```cpp
std::set<BigObject, std::less<>> myNewSet;
```

Pokud používáte výchozí Komparátor, kontejner chová stejně jako v C ++ 11 a starší.

Následující příklad ukazuje, jak přetěžovat `operator<` Chcete-li povolit uživatelům `std::set` provést vyhledávání jednoduše tak, že předávání malé řetězec, který je možné porovnat každému objektu `BigObject::id` člena.

```cpp
#include <set>
#include <string>
#include <iostream>
#include <functional>

using namespace std;

class BigObject
{
public:
    string id;
    explicit BigObject(const string& s) : id(s) {}
    bool operator< (const BigObject& other) const
    {
        return this->id < other.id;
    }

    // Other members....
};

inline bool operator<(const string& otherId, const BigObject& obj)
{
    return otherId < obj.id;
}

inline bool operator<(const BigObject& obj, const string& otherId)
{
    return obj.id < otherId;
}

int main()
{
    // Use C++14 brace-init syntax to invoke BigObject(string).
    // The s suffix invokes string ctor. It is a C++14 user-defined
    // literal defined in <string>
    BigObject b1{ "42F"s };
    BigObject b2{ "52F"s };
    BigObject b3{ "62F"s };
    set<BigObject, less<>> myNewSet; // C++14
    myNewSet.insert(b1);
    myNewSet.insert(b2);
    myNewSet.insert(b3);
    auto it = myNewSet.find(string("62F"));
    if (it != myNewSet.end())
        cout << "myNewSet element = " << it->id << endl;
    else
        cout << "element not found " << endl;

    // Keep console open in debug mode:
    cout << endl << "Press Enter to exit.";
    string s;
    getline(cin, s);
    return 0;
}

//Output: myNewSet element = 62F

```

Tyto členské funkce v mapování, multimap, sada a multiset se přetěžují pro podporu heterogenní vyhledávání:

1. find

1. count

1. lower_bound

1. upper_bound

1. equal_range

## <a name="container-adapters"></a>Adaptéry kontejneru

Adaptér kontejneru je změna pořadí nebo asociativního kontejneru, který omezuje rozhraní pro zjednodušení a srozumitelnost. Adaptéry kontejneru nepodporují iterátory.

A `queue` kontejneru následuje sémantiku FIFO (první dovnitř, první ven). První prvek *vloženo*– to znamená, vložených do fronty – je jako první se *odebrány*– to znamená odebrání z fronty. Další informace najdete v tématu [front třídy](../standard-library/queue-class.md).

A `priority_queue` kontejneru je uspořádán tak, aby prvek, který má nejvyšší hodnota je vždy první ve frontě. Další informace najdete v tématu [priority_queue – třída](../standard-library/priority-queue-class.md).

A `stack` kontejneru následuje sémantiku LIFO (poslední dovnitř, první ven). Poslední element vložený do zásobníku je odebrán první prvek. Další informace najdete v tématu [stack – třída](../standard-library/stack-class.md).

Protože adaptéry kontejneru nepodporují iterátory, nelze použít s algoritmy standardní knihovny C++. Další informace najdete v tématu [algoritmy](../standard-library/algorithms.md).

## <a name="requirements-for-container-elements"></a>Požadavky na elementy kontejnerů

Obecně prvky vloženy do kontejneru standardní knihovny C++ mohou být jakéhokoli typu objektu, pokud jsou kopírovatelné. Jen pohyblivé prvky, například ty, jako `vector<unique_ptr<T>>` , která se vytvářejí pomocí `unique_ptr<>` budou fungovat tak dlouho, dokud nebudete volat členské funkce, které se snaží kopírovat.

Destruktor není oprávněn vyvolávat výjimky.

Uspořádané asociativní kontejnery – popsané dříve v tomto článku, musí mít veřejný operátor porovnání definované. (Výchozí operátor je `operator<`, ale i typy, které nefungují s `operator<` jsou podporovány.

Některé operace s kontejnery mohou vyžadovat také veřejný výchozí konstruktor a veřejný operátor rovnocennosti. Například neuspořádané asociativní kontejnery vyžadují podporu rovnosti a použití algoritmu hash.

## <a name="accessing-container-elements"></a>Přístup k prvkům kontejneru

Prvky kontejnerů jsou přístupné pomocí iterátorů. Další informace najdete v tématu [iterátory](../standard-library/iterators.md).

> [!NOTE]
> Můžete také použít [rozsah smyčky for vycházející](../cpp/range-based-for-statement-cpp.md) iterace nad kolekcí standardní knihovny C++.

## <a name="comparing-containers"></a>Porovnání kontejnery

Všechny kontejnery přetížit operátor == pro porovnání dvou kontejnerů stejného typu, které mají stejný typ elementu. Můžete použít == k porovnání vektor\<řetězec > k jiné vektoru\<řetězec >, ale nelze jej použít k porovnání vektor\<řetězec > na seznam\<řetězec > nebo vektor\<řetězec > do vektoru \<char * >.  V C ++ 98/03 můžete [std::equal](algorithm-functions.md#equal) nebo [std::mismatch](algorithm-functions.md#mismatch) srovnávat odlišné kontejneru typy nebo typy prvků. V C ++ 11 můžete také použít [std::is_permutation](algorithm-functions.md#is_permutation). Ale v těchto případech se funkce předpokládá, že kontejnery mají stejnou délku. Pokud se druhá oblast je kratší než výsledky prvního, a potom nedefinované chování. Pokud druhá oblast je delší, výsledky může být nesprávné protože porovnání nikdy bude pokračovat za koncem první oblast.

### <a name="comparing-dissimilar-containers-c14"></a>Porovnání kontejnery odlišných typů (C ++ 14)

V C ++ 14 a později, můžete porovnat kontejnery odlišných typů a typů rozdílné prvky pomocí jedné z `std::equal`, `std::mismatch`, nebo `std::is_permutation` funkce přetížení, která berou dva rozsahy dokončení. Tato přetížení umožňují snadno porovnat kontejnerů pomocí různých délek. Tato přetížení jsou mnohem méně náchylný k chybě uživatele a jsou optimalizované vrátí hodnotu false v konstantním času, kdy jsou porovnány kontejnery rozdílné délky. Proto doporučujeme, abyste použili tato přetížení, pokud (1) máte jasný důvod nebylo, nebo (2) používáte [std::list](../standard-library/list-class.md) kontejneru, který nijak přínosné optimalizace duální rozsahy.

## <a name="see-also"></a>Viz také:

[Kontejnery](../cpp/containers-modern-cpp.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
[\<Ukázkový kontejner >](../standard-library/sample-container.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
