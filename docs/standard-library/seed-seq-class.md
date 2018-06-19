---
title: seed_seq – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::seed_seq
- random/std::seed_seq::result_type
- random/std::seed_seq::generate
- random/std::seed_seq::size
- random/std::seed_seq::param
dev_langs:
- C++
helpviewer_keywords:
- std::seed_seq [C++]
- std::seed_seq [C++], result_type
- std::seed_seq [C++], generate
- std::seed_seq [C++], size
- std::seed_seq [C++], param
ms.assetid: cba114f7-9ac6-4f2f-b773-9c84805401d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e466d8a176d5c4c7fd1e2250373b42ee263a6d4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856329"
---
# <a name="seedseq-class"></a>seed_seq – třída

Ukládá vektoru hodnot celé číslo bez znaménka, které můžete zadat náhodnou počáteční hodnoty pro modul náhodné číslo.

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

`typedef unsigned int result_type;` Typ elementů pořadí počáteční hodnoty. Typ 32bitové celé číslo bez znaménka.

## <a name="constructors"></a>Konstruktory

`seed_seq();` Výchozí konstruktor inicializuje mít prázdnou sekvencí interní.

`template<class T>` `seed_seq(initializer_list<T> initlist);` Používá `initlist` se nastavit interní pořadí.
`T` musí být celočíselného typu.

`template<class InputIterator>` `seed_seq(InputIterator begin, InputIterator end);` Inicializuje interní pořadí pomocí všechny elementy v rozsahu vstupní iterator zadat.
`iterator_traits<InputIterator>::value_type` musí být celočíselného typu.

## <a name="members"></a>Členové

### <a name="generating-functions"></a>Generování funkce

`template<class RandomAccessIterator> void generate(RandomAccessIterator begin,          RandomAccessIterator end);` Naplní elementy zadané pořadí pomocí interní algoritmus. Tento algoritmus je ovlivňován interní pořadí, pomocí kterého `seed_seq` byl inicializován.
Se nic nestane. Pokud `begin == end`.

### <a name="property-functions"></a>Funkce vlastností

`size_t size() const;` Vrátí počet prvků v `seed_seq`.

`template<class OutputIterator> void param(OutputIterator dest) const;` Zkopíruje interní pořadí do výstupní iterator `dest`.

## <a name="example"></a>Příklad

Následující příklad kódu vykonává tři konstruktory a generuje výstup ve výsledném `seed_seq` instance když přiřazeny pole. Pro příklad, který používá `seed_seq` s generátor náhodných čísel, přečtěte si téma [ \<náhodných >](../standard-library/random.md).

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

Členské funkce této třídy nevyvolá výjimku výjimky.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodných >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[\<náhodné >](../standard-library/random.md)<br/>
