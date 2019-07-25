---
title: seed_seq – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::seed_seq
- random/std::seed_seq::result_type
- random/std::seed_seq::generate
- random/std::seed_seq::size
- random/std::seed_seq::param
helpviewer_keywords:
- std::seed_seq [C++]
- std::seed_seq [C++], result_type
- std::seed_seq [C++], generate
- std::seed_seq [C++], size
- std::seed_seq [C++], param
ms.assetid: cba114f7-9ac6-4f2f-b773-9c84805401d6
ms.openlocfilehash: d2dc561a9160188507a61ec3734cfbf9f3e74199
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450513"
---
# <a name="seedseq-class"></a>seed_seq – třída

Ukládá vektor hodnot unsigned integer, které mohou poskytovat náhodnou počáteční hodnotu pro modul náhodného číslování.

## <a name="syntax"></a>Syntaxe

```cpp
class seed_seq
   {
public:
   // types
   typedef unsigned int result_type;

   // constructors
   seed_seq();
   template <class T>
      seed_seq(initializer_list<T> initlist);
   template <class InputIterator>
      seed_seq(InputIterator begin, InputIterator end);

   // generating functions
   template <class RandomAccessIterator>
      void generate(RandomAccessIterator begin, RandomAccessIterator end);

   // property functions
   size_t size() const;
   template <class OutputIterator>
      void param(OutputIterator dest) const;

   // no copy functions
   seed_seq(const seed_seq&) = delete;
   void operator=(const seed_seq&) = delete;
   };
```

## <a name="types"></a>Typy

```cpp
typedef unsigned int result_type;
```

Typ prvků sekvence počáteční hodnoty. 32 typ bitové unsigned integer.

## <a name="constructors"></a>Konstruktory

```cpp
seed_seq();
```

Výchozí konstruktor inicializuje, aby měl prázdnou interní sekvenci.

```cpp
template<class T>
seed_seq(initializer_list<T> initlist);
```

Používá `initlist` k nastavení interní sekvence.
`T`musí se jednat o celočíselný typ.

```cpp
template<class InputIterator>
seed_seq(InputIterator begin, InputIterator end);
```

Inicializuje vnitřní sekvenci pomocí všech prvků v poskytnutém vstupním rozsahu iterátoru.
`iterator_traits<InputIterator>::value_type`musí se jednat o celočíselný typ.

## <a name="members"></a>Členové

### <a name="generating-functions"></a>Generování funkcí

```cpp
template<class RandomAccessIterator>
void generate(RandomAccessIterator begin,
          RandomAccessIterator end);
```

Naplní prvky poskytnuté sekvence pomocí interního algoritmu. Tento algoritmus je ovlivněn vnitřní sekvencí, která `seed_seq` byla inicializována.
Neprovede žádnou akci `begin == end`, pokud.

### <a name="property-functions"></a>Funkce vlastností

```cpp
size_t size() const;
```

Vrátí počet prvků v `seed_seq`.

```cpp
template<class OutputIterator>
void param(OutputIterator dest) const;
```

Zkopíruje interní sekvenci do výstupního iterátoru `dest`.

## <a name="example"></a>Příklad

Následující příklad kódu vykonává tři konstruktory a generuje výstup z výsledných `seed_seq` instancí, pokud jsou přiřazeny k poli. Příklad, který používá `seed_seq` s generátorem náhodných čísel, naleznete v tématu [ \<Random >](../standard-library/random.md).

```cpp
#include <iostream>
#include <random>
#include <string>
#include <array>

using namespace std;

void test(const seed_seq& sseq) {
    cout << endl << "seed_seq::size(): " << sseq.size() << endl;

    cout << "seed_seq::param(): ";
    ostream_iterator<unsigned int> out(cout, " ");
    sseq.param(out);
    cout << endl;

    cout << "Generating a sequence of 5 elements into an array: " << endl;
    array<unsigned int, 5> seq;
    sseq.generate(seq.begin(), seq.end());
    for (unsigned x : seq) { cout << x << endl; }
}

int main()
{
    seed_seq seed1;
    test(seed1);

    seed_seq seed2 = { 1701, 1729, 1791 };
    test(seed2);

    string sstr = "A B C D"; // seed string
    seed_seq seed3(sstr.begin(), sstr.end());
    test(seed3);
}
```

```Output
seed_seq::size(): 0
seed_seq::param():
Generating a sequence of 5 elements into an array:
505382999
163489202
3932644188
763126080
73937346

seed_seq::size(): 3
seed_seq::param(): 1701 1729 1791
Generating a sequence of 5 elements into an array:
1730669648
1954224479
2809786021
1172893117
2393473414

seed_seq::size(): 7
seed_seq::param(): 65 32 66 32 67 32 68
Generating a sequence of 5 elements into an array:
3139879222
3775111734
1084804564
2485037668
1985355432
```

## <a name="remarks"></a>Poznámky

Členské funkce této třídy nevyvolávají výjimky.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<náhodné >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)
