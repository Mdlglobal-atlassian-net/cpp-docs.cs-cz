---
title: Standardní C++ knihovny kontejnery | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C++ Standard Library, template class containers
- containers, C++ Standard Library
ms.assetid: 8e915ca1-19ba-4f0d-93c8-e2c3bfd638eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd851ae3cf47ca260b1923d969123b21293d8623
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862426"
---
# <a name="c-standard-library-containers"></a>Kontejnery knihovny C++ Standard

Standardní knihovna obsahuje různé kontejnery bezpečnost typů ukládání kolekcí související objekty. Kontejnery jsou šablony třídy; Když je deklarovat proměnnou kontejneru, můžete zadat typ prvků, které bude obsahovat kontejneru. Kontejnery konstruovat s inicializační seznamy. Mají členské funkce pro přidávání a odebírání elementů a provádění dalších operací.

Iterace v elementy v kontejneru a přístup k jednotlivé elementy pomocí [iterátory](../standard-library/iterators.md). Iterátory můžete použít explicitně pomocí svých členských funkcí a operátory stejně jako globální funkce. Můžete také použít je implicitně, například pomocí rozsah-pro smyčky. Iterátory pro všechny kontejnery standardní knihovna C++ mají společné rozhraní, ale každý kontejner definuje vlastní specializované iterátory.

Kontejnery je možné rozdělit do tří kategorií: pořadí kontejnery, asociativní kontejnerů a kontejner adaptéry.

## <a name="sequence_containers"></a> Pořadí kontejnery

Kontejnery pořadí zachovávají řazení vložené prvky zda jste zadali.

A `vector` kontejneru se chová jako pole, ale můžou automaticky růst podle potřeby. Je náhodný přístup a souvisle uložené, a délka je vysoce flexibilní. Z těchto důvodů a informace `vector` je kontejner upřednostňované pořadí pro většinu aplikací. Pokud máte pochybnosti, jaký typ kontejneru pořadí použití, spusťte pomocí vektor! Další informace najdete v tématu [vector – třída](../standard-library/vector-class.md).

`array` Kontejner obsahuje některé z výhod `vector`, ale není tak účinná délka. Další informace najdete v tématu [array – třída](../standard-library/array-class-stl.md).

A `deque` kontejneru (dvěma konci queue) umožňuje rychlé vložení a odstranění na začátku a konci kontejneru. Sdílí výhody náhodný přístup a flexibilní délky `vector`, ale není souvislé. Další informace najdete v tématu [deque – třída](../standard-library/deque-class.md).

A `list` kontejneru je dvakrát propojený seznam, který umožňuje obousměrnou přístup, rychlé vložení a rychlé odstranění kdekoli v kontejneru, ale nemůže náhodně přístup k elementu v kontejneru. Další informace najdete v tématu [list – třída](../standard-library/list-class.md).

A `forward_list` kontejner je jednotlivě propojený seznam – předat dál přístup verzi `list`. Další informace najdete v tématu [forward_list – třída](../standard-library/forward-list-class.md).

## <a name="associative-containers"></a>Asociativní kontejnery

V asociativní kontejnery, jsou vloženy elementy předem definovaným pořadím – například jako seřazená vzestupně. Neseřazený asociativní kontejnery jsou k dispozici. Asociativní kontejnery lze rozdělit do dvou podmnožin: mapuje a nastaví.

A `map`, někdy označují jako slovník, se skládá z dvojice klíč/hodnota. Klíč slouží k uspořádání pořadí a hodnota souvisí s tímto klíčem. Například `map` může obsahovat klíče, které představují každý jedinečný slova v text a odpovídající hodnoty, které představují počet pokusů, které se zobrazí jednotlivých slov v textu. Neseřazený verze `map` je `unordered_map`. Další informace najdete v tématu [map – třída](../standard-library/map-class.md) a [unordered_map – třída](../standard-library/unordered-map-class.md).

A `set` je právě vzestupným kontejner jedinečný elementy – hodnota je také klíč. Neseřazený verze `set` je `unordered_set`. Další informace najdete v tématu [set – třída](../standard-library/set-class.md) a [unordered_set – třída](../standard-library/unordered-set-class.md).

Obě `map` a `set` Povolit jenom jednu instanci klíče nebo elementu, který chcete vložit do kontejneru. Pokud je potřeba víc instancí elementů, použijte `multimap` nebo `multiset`. Je neuspořádaného verze `unordered_multimap` a `unordered_multiset`. Další informace najdete v tématu [multimap – třída](../standard-library/multimap-class.md), [unordered_multimap – třída](../standard-library/unordered-multimap-class.md), [multiset – třída](../standard-library/multiset-class.md), a [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).

Seřazené mapy a nastaví podporují obousměrný iterátory a jejich neuspořádaný protějšky podporují dopředného iterátory. Další informace najdete v tématu [iterátory](../standard-library/iterators.md).

### <a name="heterogeneous-lookup-in-associative-containers-c14"></a>Heterogenní vyhledávání v asociativní kontejnery (C ++ 14)

Seřazené asociativní kontejnery (mapy, multimap, sady a multimnožina) teď heterogenní podpora vyhledávání, což znamená, že už nejste potřeba předat přesně stejný typ objektu jako klíč nebo element v členské funkce, jako `find()` a `lower_bound()` . Místo toho můžete předat libovolný typ, pro kterou přetížené `operator<` je definována umožňující porovnání se typ klíče.

Je povoleno heterogenous vyhledávání na základě přihlášení, když zadáte `std::less<>` nebo `std::greater<>` "diamond functor" komparátoru při deklarace proměnné kontejneru, jak je vidět tady:

```cpp
std::set<BigObject, std::less<>> myNewSet;
```

Pokud chcete použít výchozí Komparátor, kontejneru se chová, stejně jako v C ++ 11 a starší.

Následující příklad ukazuje, jak přetížení `operator<` Chcete-li povolit uživatelům `std::set` provedete hledání jednoduše tak, že předávání malé řetězec, který je možné porovnávat pro každý objekt `BigObject::id` člen.

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

Následující členské funkce v mapování, multimap, sady a multimnožina mít byl přetížený pro podporu heterogenní vyhledávání:

1. find

1. count

1. lower_bound

1. upper_bound

1. equal_range

## <a name="container-adapters"></a>Adaptéry kontejneru

Adaptér kontejneru se odlišuje od pořadí nebo asociativní kontejner, který omezuje rozhraní, jednoduchost a srozumitelnější. Kontejner adaptéry nepodporují iterátory.

A `queue` kontejneru následuje sémantiku FIFO (první do, první out). První prvek *nabídnutých*– to znamená, vložených do fronty – je první být *odebrány*– to znamená, odebraných z fronty. Další informace najdete v tématu [queue – třída](../standard-library/queue-class.md).

A `priority_queue` kontejneru je organizovaná tak, aby elementu, který má nejvyšší hodnotou je vždy první ve frontě. Další informace najdete v tématu [priority_queue – třída](../standard-library/priority-queue-class.md).

A `stack` kontejneru následuje sémantiku LIFO (last in, out první). Posledním elementem nabídnutých v zásobníku je první prvek odebrány. Další informace najdete v tématu [stack – třída](../standard-library/stack-class.md).

Protože kontejner adaptéry nepodporují iterátory, nelze použít s algoritmy standardní knihovna C++. Další informace najdete v tématu [algoritmy](../standard-library/algorithms.md).

## <a name="requirements-for-container-elements"></a>Požadavky na elementy kontejneru

Obecně platí může být prvky vloženy do kontejneru standardní knihovna C++ jakéhokoli typu objektu, pokud jsou kopírovatelná. Elementy jen Movable – například ty, například `vector<unique_ptr<T>>` které jsou vytvořené pomocí `unique_ptr<>` bude fungovat, dokud není volat členské funkce, které se pokoušejí o zkopírujte je.

Destruktoru nemá oprávnění k výjimku.

Seřazené asociativní kontejnery – popsané výše v tomto článku – musí mít definovaný operátor porovnání veřejné. (Ve výchozím nastavení, operátor je `operator<`, ale i typy, které nefungují s `operator<` jsou podporovány.

Některé operace kontejnerům může také vyžadovat veřejný výchozí konstruktor a veřejné ekvivalenční operátor. Například neuspořádaný asociativní kontejnery vyžaduje podporu algoritmu hash a rovnosti.

## <a name="accessing-container-elements"></a>Přístup k elementy kontejneru

Elementy kontejnerů jsou přístupné pomocí iterátory. Další informace najdete v tématu [iterátory](../standard-library/iterators.md).

> [!NOTE]
> Můžete také použít [na základě rozsahu smyčky for](../cpp/range-based-for-statement-cpp.md) Iterujte přes standardní knihovna C++ kolekce.

## <a name="comparing-containers"></a>Porovnání kontejnery

Všechny kontejnery přetížení operátoru == pro porovnání dvou kontejnery stejného typu, které mají stejný typ elementu. Můžete použít k porovnání vektor ==\<řetězec > k jiným způsobem\<řetězec >, ale nemůžete ji použít k porovnání vektor\<řetězec > do seznamu\<řetězec > nebo vektor\<řetězec > na vektor \<char * >.  Můžete v C ++ 98/03 [std::equal](algorithm-functions.md#equal) nebo [std::mismatch](algorithm-functions.md#mismatch) k porovnání kontejneru odlišné typy nebo typy elementů. V C ++ 11 můžete také použít [std::is_permutation](algorithm-functions.md#is_permutation). Ale v těchto případech funkce předpokládá, že kontejnery mají stejnou délku. Pokud je kratší než výsledky první pak nedefinované chování druhého rozsahu. Pokud již druhého rozsahu, výsledky může být nesprávný protože porovnání nikdy pokračuje za koncem první rozsahu.

### <a name="comparing-dissimilar-containers-c14"></a>Porovnání odlišné kontejnery (C ++ 14)

C ++ 14 a novější, můžete porovnat odlišné kontejnery nebo odlišných typů elementů typů pomocí jedné z **std::equal**, **std::mismatch**, nebo **std::is_permutation**funkce přetížení, které provést dvě dokončení rozsahy. Tato přetížení umožňují porovnat kontejnery s různých délek. Tato přetížení jsou mnohem méně náchylný k chybě uživatele a jsou optimalizované vrátí hodnotu false v konstantní čas, kdy jsou porovnávány kontejnery odlišné délky. Proto doporučujeme, abyste používali tyto přetížení, pokud (1) máte velmi jasně důvod nikoli k, nebo (2) používáte [std::list](../standard-library/list-class.md) kontejneru, který není těžit z výhod duální rozsahy optimalizace.

## <a name="see-also"></a>Viz také

[Kontejnery](../cpp/containers-modern-cpp.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
[\<Ukázkový kontejner >](../standard-library/sample-container.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
