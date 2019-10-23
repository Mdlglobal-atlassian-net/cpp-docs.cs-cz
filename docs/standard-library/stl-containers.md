---
title: C++Kontejnery knihovny Standard
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, class template containers
- containers, C++ Standard Library
ms.assetid: 8e915ca1-19ba-4f0d-93c8-e2c3bfd638eb
ms.openlocfilehash: 1119947534c030afaad64e4905e58365ffffd05e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686095"
---
# <a name="c-standard-library-containers"></a>C++Kontejnery knihovny Standard

Standardní knihovna poskytuje různé kontejnery pro bezpečné typy pro ukládání kolekcí souvisejících objektů. Kontejnery jsou šablony třídy; Při deklaraci proměnné kontejneru zadáte typ prvků, které kontejner bude obsahovat. Kontejnery lze sestavit pomocí seznamů inicializátorů. Mají členské funkce pro přidávání a odebírání prvků a provádění jiných operací.

Můžete iterovat prvky v kontejneru a přistupovat k jednotlivým prvkům pomocí [iterátorů](../standard-library/iterators.md). Iterátory můžete použít explicitně pomocí jejich členských funkcí a operátorů a také globálních funkcí. Můžete je také implicitně použít například pomocí smyčky Range-for. Iterátory pro všechny C++ kontejnery standardní knihovny mají společné rozhraní, ale každý kontejner definuje vlastní specializované iterátory.

Kontejnery lze rozdělit do tří kategorií: kontejnery sekvence, asociativní kontejnery a adaptéry kontejnerů.

## <a name="sequence_containers"></a>Kontejnery sekvence

Kontejnery sekvence udržují řazení vložených prvků, které zadáte.

Kontejner `vector` se chová jako pole, ale může automaticky růst podle potřeby. Je to náhodný přístup a souvisle uložený a délka je vysoce flexibilní. Z těchto důvodů a dalších `vector` je upřednostňovaným kontejnerem sekvencí pro většinu aplikací. V případě pochybností o tom, jaký druh kontejneru sekvence se má použít, začněte pomocí vektoru! Další informace naleznete v tématu [Třída Vector](../standard-library/vector-class.md).

@No__t_0 kontejner obsahuje některé síly `vector`, ale délka není tak flexibilní. Další informace naleznete v tématu [Třída Array](../standard-library/array-class-stl.md).

Kontejner `deque` (fronta se dvěma konci) umožňuje rychlé vkládání a odstraňování na začátku a konci kontejneru. Sdílí výhody `vector` s náhodným přístupem a flexibilní délkou, ale nesousedí. Další informace naleznete v tématu [Třída deque](../standard-library/deque-class.md).

Kontejner `list` je dvakrát propojený seznam, který umožňuje obousměrný přístup, rychlé vkládání a rychlé mazání kdekoli v kontejneru, ale nemůžete náhodně přistupovat k elementu v kontejneru. Další informace naleznete v tématu [Třída list](../standard-library/list-class.md).

Kontejner `forward_list` je jednotlivě propojený seznam – verze pro dopředné připojení `list`. Další informace naleznete v tématu [Třída forward_list](../standard-library/forward-list-class.md).

## <a name="associative-containers"></a>Asociativní kontejnery

V asociativních kontejnerech jsou prvky vloženy do předem definovaného pořadí, například jako řazení vzestupně. K dispozici jsou také neuspořádané asociativní kontejnery. Asociativní kontejnery mohou být seskupeny do dvou podmnožin: mapy a sady.

@No__t_0, který se někdy označuje jako slovník, se skládá z páru klíč/hodnota. Klíč se používá k seřazení sekvence a hodnota je spojena s tímto klíčem. @No__t_0 například může obsahovat klíče, které reprezentují každé jedinečné slovo v textu a odpovídající hodnoty, které reprezentují počet zobrazených slov v textu. Neuspořádaná verze `map` je `unordered_map`. Další informace naleznete v tématu [map Class](../standard-library/map-class.md) a [unordered_map Class](../standard-library/unordered-map-class.md).

@No__t_0 je pouze vzestupné kontejner jedinečných prvků – hodnota je také klíč. Neuspořádaná verze `set` je `unordered_set`. Další informace naleznete v tématu [set Class](../standard-library/set-class.md) a [unordered_set Class](../standard-library/unordered-set-class.md).

@No__t_0 i `set` umožňují vložit do kontejneru pouze jednu instanci klíče nebo elementu. Je-li vyžadováno více instancí prvků, použijte `multimap` nebo `multiset`. Neuspořádané verze jsou `unordered_multimap` a `unordered_multiset`. Další informace naleznete v tématu [Třída multimap](../standard-library/multimap-class.md), třída [unordered_multimap](../standard-library/unordered-multimap-class.md), třída [multiset](../standard-library/multiset-class.md)a [unordered_multiset třídy](../standard-library/unordered-multiset-class.md).

Seřazené mapy a sady podporují obousměrné iterátory a jejich neuspořádané protějšky podporují předávací iterátory. Další informace najdete v tématu [iterátory](../standard-library/iterators.md).

### <a name="heterogeneous-lookup-in-associative-containers-c14"></a>Heterogenní vyhledávání v asociativních kontejnerech (C++ 14)

Seřazené asociativní kontejnery (map, multimap, set a multiset) teď podporují heterogenní vyhledávání, což znamená, že už nemusíte předávat přesný stejný typ objektu jako klíč nebo element v členských funkcích, jako je například `find()` a `lower_bound()`. Místo toho můžete předat libovolný typ, pro který je definován přetížený `operator<`, který umožňuje porovnání s typem klíče.

Vyhledávání heterogenní je povoleno na základě výslovného souhlasu při zadání `std::less<>` nebo `std::greater<>` "Diamond funktor" komparátor při deklaraci proměnné kontejneru, jak je znázorněno zde:

```cpp
std::set<BigObject, std::less<>> myNewSet;
```

Použijete-li výchozí komparátor, kontejner se chová přesně stejně jako v jazyce C++ 11 a starších.

Následující příklad ukazuje, jak přetížit `operator<`, aby mohli uživatelé `std::set` provádět vyhledávání jednoduše předáním malého řetězce, který lze porovnat s `BigObject::id`m členem každého objektu.

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

Následující členské funkce v mapě, multimap, set a multiset byly přetíženy, aby podporovaly heterogenní vyhledávání:

1. find

1. count

1. lower_bound

1. upper_bound

1. equal_range

## <a name="container-adapters"></a>Adaptéry kontejneru

Adaptér kontejneru je variace sekvence nebo asociativního kontejneru, který omezuje rozhraní pro jednoduchost a přehlednost. Adaptéry kontejneru nepodporují iterátory.

@No__t_0 kontejner následuje sémantika FIFO (první v, první ven). První *prvek, který je vložen do*fronty, je první, který *má být odebrán, který*je odebrán z fronty. Další informace najdete v tématu [Třída Queue](../standard-library/queue-class.md).

Kontejner `priority_queue` je uspořádán tak, že prvek, který má nejvyšší hodnotu, je vždy první ve frontě. Další informace naleznete v tématu [Třída priority_queue](../standard-library/priority-queue-class.md).

@No__t_0 kontejner následuje sémantika LIFO (poslední v, první ven). Poslední prvek přesunutý do zásobníku je prvním prvkem, který byl odebrán. Další informace naleznete v tématu [Třída zásobníku](../standard-library/stack-class.md).

Protože adaptéry kontejneru nepodporují iterátory, nelze je použít se C++ standardními algoritmy knihovny. Další informace najdete v tématu [algoritmy](../standard-library/algorithms.md).

## <a name="requirements-for-container-elements"></a>Požadavky na prvky kontejneru

Obecně prvky vložené do kontejneru C++ standardní knihovny mohou být pouze pro libovolný typ objektu, pokud jsou zkopírovány. Pouze pohyblivé prvky, například `vector<unique_ptr<T>>`, které jsou vytvořeny pomocí `unique_ptr<>`, budou fungovat, pokud nebudete volat členské funkce, které se pokoušejí zkopírovat.

Destruktor není oprávněn vyvolat výjimku.

Seřazené asociativní kontejnery – popsané dříve v tomto článku – musí mít definovaný veřejný operátor porovnání. (Ve výchozím nastavení je operátor `operator<`, ale i typy, které nefungují s `operator<` jsou podporovány.

Některé operace na kontejnerech mohou také vyžadovat veřejný výchozí konstruktor a veřejný operátor rovnosti. Například neuspořádané asociativní kontejnery vyžadují podporu rovnosti a algoritmu hash.

## <a name="accessing-container-elements"></a>Přístup k elementům kontejneru

K prvkům kontejneru se dostanete pomocí iterátorů. Další informace najdete v tématu [iterátory](../standard-library/iterators.md).

> [!NOTE]
> Můžete také použít [smyčky na základě rozsahu](../cpp/range-based-for-statement-cpp.md) pro iteraci na C++ standardních kolekcích knihoven.

## <a name="comparing-containers"></a>Porovnávání kontejnerů

Všechny kontejnery přetěžují operátor = = pro porovnání dvou kontejnerů stejného typu, které mají stejný typ elementu. Pomocí = = můžete porovnat \<string vektoru > na jiný vektor \<string >, ale nemůžete ho použít k porovnání vektoru \<string > se seznamem \<string > nebo vektor \<string > ke vektorové \<char * >.  V C++ 98/03 můžete použít [std:: EQUAL](algorithm-functions.md#equal) nebo [std:: Neshoda](algorithm-functions.md#mismatch) pro porovnání odlišných typů kontejnerů nebo typů prvků. V C++ 11 můžete také použít [std:: is_permutation](algorithm-functions.md#is_permutation). Ale ve všech těchto případech funkce předpokládají, že kontejnery mají stejnou délku. Pokud je druhý rozsah kratší než první, pak nedefinované výsledky chování. Pokud je druhý rozsah delší, výsledky mohou být stále nesprávné, protože porovnání nikdy nepokračuje po konci prvního rozsahu.

### <a name="comparing-dissimilar-containers-c14"></a>Porovnávání nepodobných kontejnerů (C++ 14)

V C++ 14 a novějších můžete porovnat nepodobné kontejnery nebo odlišné typy prvků pomocí jednoho z `std::equal`, `std::mismatch` `std::is_permutation` nebo přetížení funkcí, které přijímají dva úplné rozsahy. Tato přetížení umožňují porovnat kontejnery s různou délkou. Tato přetížení jsou mnohem méně náchylná k chybě uživatele a jsou optimalizované tak, aby vracely hodnotu false v konstantní době, kdy se porovnávají kontejnery s podobnými délkami. Proto doporučujeme použít tato přetížení, pokud (1) máte velmi jasný důvod not to, nebo (2) používáte kontejner [std:: list](../standard-library/list-class.md) , který není výhodou optimalizace duálního rozsahu.

## <a name="see-also"></a>Viz také:

@No__t_1 [kontejnerů](../cpp/containers-modern-cpp.md)
Referenční \ standardní knihovny [ C++ ](../standard-library/cpp-standard-library-reference.md)
[\<sample > kontejneru](../standard-library/sample-container.md) \
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
