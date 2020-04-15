---
title: Kontejnery standardní knihovny c++
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, class template containers
- containers, C++ Standard Library
ms.assetid: 8e915ca1-19ba-4f0d-93c8-e2c3bfd638eb
ms.openlocfilehash: 01be754dd7b418f64cf495d7563f65b323265df8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376705"
---
# <a name="c-standard-library-containers"></a>Kontejnery standardní knihovny c++

Standardní knihovna poskytuje různé kontejnery bezpečné pro typ pro ukládání kolekcí souvisejících objektů. Kontejnery jsou šablony tříd. Když deklarujete proměnnou kontejneru, určíte typ prvků, které bude kontejner obsahovat. Kontejnery mohou být vytvořeny pomocí seznamů inicializátoru. Mají členské funkce pro přidávání a odebírání prvků a provádění dalších operací.

Iterovat přes prvky v kontejneru a přístup k jednotlivým prvkům pomocí [iterátory](../standard-library/iterators.md). Iterátory můžete použít explicitně pomocí jejich členských funkcí a operátorů a globálních funkcí. Můžete je také použít implicitně, například pomocí smyčky range-for. Iterátory pro všechny kontejnery standardní knihovny Jazyka C++ mají společné rozhraní, ale každý kontejner definuje své vlastní specializované iterátory.

Kontejnery lze rozdělit do tří kategorií: sekvence kontejnery, asociativní kontejnery a kontejneradaptéry.

## <a name="sequence-containers"></a><a name="sequence_containers"></a>Sekvenční kontejnery

Sekvence kontejnery udržovat řazení vložené prvky, které zadáte.

Kontejner `vector` se chová jako pole, ale může automaticky růst podle potřeby. Je náhodný přístup a souvislé uloženy a délka je vysoce flexibilní. Z těchto důvodů `vector` a další, je upřednostňovaný kontejner sekvence pro většinu aplikací. Pokud si nejste vědomi toho, jaký druh sekvenčního kontejneru použít, začněte pomocí vektoru! Další informace naleznete v tématu [vector Class](../standard-library/vector-class.md).

Kontejner `array` má některé silné `vector`stránky , ale délka není tak flexibilní. Další informace naleznete [v tématu matice Class](../standard-library/array-class-stl.md).

Kontejner `deque` (dvojitá fronta) umožňuje rychlé vložení a odstranění na začátku a na konci kontejneru. Sdílí výhody náhodného přístupu `vector`a flexibilní délky aplikace , ale není souvislá. Další informace naleznete [v tématu deque Class](../standard-library/deque-class.md).

Kontejner `list` je dvakrát propojený seznam, který umožňuje obousměrný přístup, rychlé vkládání a rychlé odstranění kdekoli v kontejneru, ale nemůžete náhodně přistupovat k prvku v kontejneru. Další informace naleznete v [seznamu Class](../standard-library/list-class.md).

Kontejner `forward_list` je singly propojený seznam – verze `list`aplikace . Další informace naleznete [v tématu forward_list Class](../standard-library/forward-list-class.md).

## <a name="associative-containers"></a>Asociativní kontejnery

V asociativních kontejnerech jsou prvky vloženy v předdefinovaném pořadí – například jako seřazené vzestupně. K dispozici jsou také neuspořádané asociativní kontejnery. Asociativní kontejnery lze seskupit do dvou podmnožiny: mapy a sady.

A `map`, někdy označované jako slovník, se skládá z dvojice klíč/hodnota. Klíč se používá k pořadí sekvence a hodnota je přidružena k tomuto klíči. Může `map` například obsahovat klíče, které představují každé jedinečné slovo v textu a odpovídající hodnoty, které představují počet zobrazení každého slova v textu. Neuspořádaná verze `map` `unordered_map`programu je . Další informace naleznete v [tématu mapa třídy](../standard-library/map-class.md) a [unordered_map třídy](../standard-library/unordered-map-class.md).

A `set` je pouze vzestupný kontejner jedinečných prvků – hodnota je také klíčem. Neuspořádaná verze `set` `unordered_set`programu je . Další informace naleznete v [tématu set Class](../standard-library/set-class.md) a [unordered_set Class](../standard-library/unordered-set-class.md).

Oba `map` `set` a povolit pouze jednu instanci klíče nebo prvku, které mají být vloženy do kontejneru. Pokud je vyžadováno více instancí prvků, použijte `multimap` nebo `multiset`. Neuspořádané verze `unordered_multimap` jsou `unordered_multiset`a . Další informace naleznete v [tématu multimap Class](../standard-library/multimap-class.md), [unordered_multimap Class](../standard-library/unordered-multimap-class.md), [multiset Class](../standard-library/multiset-class.md)a unordered_multiset [Class](../standard-library/unordered-multiset-class.md).

Objednané mapy a sady podporují obousměrné iterátory a jejich neuspořádané protějšky podporují dopředu iterátory. Další informace naleznete v tématu [Iterators](../standard-library/iterators.md).

### <a name="heterogeneous-lookup-in-associative-containers-c14"></a>Heterogenní vyhledávání v asociativních kontejnerech (C++14)

Objednané asociativní kontejnery (mapa, multimap, set a multiset) nyní podporují heterogenní vyhledávání, což znamená, že již nemusíte předávat přesně `find()` stejný `lower_bound()`typ objektu jako klíč nebo prvek v členských funkcích, jako jsou a . Místo toho můžete předat libovolný typ, `operator<` pro který je definován přetížený, který umožňuje porovnání s typem klíče.

Heterogenní vyhledávání je povoleno na základě opt-in, `std::less<>` když `std::greater<>` zadáte nebo "diamond functor" komparátor při deklarování proměnné kontejneru, jak je znázorněno zde:

```cpp
std::set<BigObject, std::less<>> myNewSet;
```

Pokud použijete výchozí komparátor, pak kontejner chová přesně tak, jak tomu bylo v Jazyce C ++ 11 a starší.

Následující příklad ukazuje, `operator<` jak přetížení povolit uživatelům vyhledávání `std::set` provést jednoduše předáním v malém řetězci, který `BigObject::id` lze porovnat s členem každého objektu.

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

Následující členské funkce v mapách, multimap, set a multiset byly přetíženy na podporu heterogennívyhledávání:

1. find

1. count

1. lower_bound

1. upper_bound

1. equal_range

## <a name="container-adapters"></a>Adaptéry kontejneru

Adaptér kontejneru je varianta sekvence nebo asociativní kontejner, který omezuje rozhraní pro jednoduchost a srozumitelnost. Adaptéry kontejneru nepodporují iterátory.

Kontejner `queue` následuje FIFO (první dovnitř, první ven) sémantiku. První *prvek, který*je vložen do fronty, je první, který má být *odebrán*– to znamená, že je odebrán z fronty. Další informace naleznete v [tématu třída fronty](../standard-library/queue-class.md).

Kontejner `priority_queue` je uspořádán tak, že prvek, který má nejvyšší hodnotu, je vždy první ve frontě. Další informace naleznete [v tématu priority_queue Class](../standard-library/priority-queue-class.md).

Kontejner `stack` následuje LIFO (poslední dovnitř, první ven) sémantiku. Poslední prvek tlačil v zásobníku je první prvek popped. Další informace naleznete v [tématu stack Class](../standard-library/stack-class.md).

Vzhledem k tomu, že adaptéry kontejneru nepodporují iterátory, nelze je použít s algoritmy standardní knihovny jazyka C++. Další informace naleznete v [tématu Algoritmy](../standard-library/algorithms.md).

## <a name="requirements-for-container-elements"></a>Požadavky na prvky kontejneru

Obecně platí, že prvky vložené do kontejneru standardní knihovny jazyka C++ mohou mít téměř libovolný typ objektu, pokud jsou kopírovatelné. Movité prvky – například ty, jako `vector<unique_ptr<T>>` jsou `unique_ptr<>` vytvořeny pomocí bude fungovat tak dlouho, dokud nevoláčlenské funkce, které se pokoušejí zkopírovat.

Destruktor není povoleno vyvolat výjimku.

Objednané asociativní kontejnery – popsané dříve v tomto článku – musí mít definovaný operátor veřejného porovnání. (Ve výchozím nastavení `operator<`je podporován operátor , ale `operator<` podporovány jsou i typy, které nepracují.

Některé operace na kontejnery může také vyžadovat veřejné výchozí konstruktor a operátor veřejné ekvivalence. Například neuspořádané asociativní kontejnery vyžadují podporu pro rovnost a hašování.

## <a name="accessing-container-elements"></a>Přístup k prvkům kontejneru

Prvky kontejnerů jsou přístupné pomocí iterátorů. Další informace naleznete v tématu [Iterators](../standard-library/iterators.md).

> [!NOTE]
> Můžete také použít [rozsah založené na smyčkách](../cpp/range-based-for-statement-cpp.md) iterát přes c++ standardní knihovny kolekce.

## <a name="comparing-containers"></a>Porovnání kontejnerů

Všechny kontejnery přetížení operator== pro porovnání dvou kontejnerů stejného typu, které mají stejný typ prvku. Můžete použít == porovnat\<> vektorového\<řetězce s jiným> vektorového řetězce,\<ale nemůžete ho\<použít k\<porovnání> vektorového řetězce s řetězcem seznamu> nebo> vektorového řetězce s vektorovým\<znakem*>.  V jazyce C++98/03 můžete použít [std::equal](algorithm-functions.md#equal) nebo [std::neshoda](algorithm-functions.md#mismatch) k porovnání odlišných typů kontejnerů a/nebo typů prvků. V jazyce C++11 můžete také použít [std::is_permutation](algorithm-functions.md#is_permutation). Ale ve všech těchto případech funkce předpokládají, že kontejnery mají stejnou délku. Pokud druhý rozsah je kratší než první, pak nedefinované chování výsledky. Pokud druhý rozsah je delší, výsledky mohou být stále nesprávné, protože porovnání nikdy pokračuje za koncem první oblasti.

### <a name="comparing-dissimilar-containers-c14"></a>Porovnání odlišných kontejnerů (C++14)

V jazyce C++ 14 a novějším můžete porovnat odlišné kontejnery nebo odlišné `std::equal` `std::mismatch`typy `std::is_permutation` prvků pomocí jednoho z přetížení , nebo funkce, které zabírají dva úplné rozsahy. Tato přetížení umožňují porovnat kontejnery s různými délkami. Tato přetížení jsou mnohem méně náchylné k chybě uživatele a jsou optimalizovány pro vrácení false v konstantním čase při porovnání kontejnerů odlišných délek. Proto doporučujeme použít tyto přetížení, pokud máte jasný důvod, proč ne, nebo používáte [std::list](../standard-library/list-class.md) kontejneru, který nemá prospěch z optimalizace duálního rozsahu.

## <a name="see-also"></a>Viz také

[Paralelní kontejnery](../parallel/concrt/parallel-containers-and-objects.md)\
[\<>nádoby se vzorky](../standard-library/sample-container.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
