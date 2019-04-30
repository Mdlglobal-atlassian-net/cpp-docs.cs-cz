---
title: Algoritmy (moderní verze jazyka C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
ms.openlocfilehash: b972e575c982ae2523ec560a6237eac76ceaf834
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345179"
---
# <a name="algorithms-modern-c"></a>Algoritmy (moderní verze jazyka C++)

Pro moderní programování C++ doporučujeme použít algoritmy [standardní knihovny C++](../standard-library/cpp-standard-library-reference.md). Tady jsou některé důležité příklady:

- **for_each**, což je výchozí algoritmus pro procházení. (Také **transformace** pro sémantiku není na místě.)

- **find_if**, což je výchozí algoritmus pro hledání.

- **řazení**, **lower_bound**a ostatní výchozí algoritmy řazení a vyhledávání.

Pro zápis Komparátor, použijte přísné **<** a používat *pojmenované lambda výrazy* kde je to možné.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="loops"></a>Smyčky

Pokud je to možné, použijte založený na rozsahu **pro** smyčky nebo volání algoritmu nebo obojí místo ručně psané smyčky. **kopírování**, **transformace**, **count_if**, **remove_if –**, a ostatní jim podobné jsou mnohem lepší než psané smyčky, protože jejich záměr je zřejmý a usnadňují zápis kódu bez chyb. Také mnoho algoritmů standardní knihovny C++ mají Optimalizace implementace, které je zefektivňují.

Namísto starého C++ následujícím způsobem:

```cpp
for ( auto i = strings.begin(); i != strings.end(); ++i ) {
    /* ... */
}

auto i = v.begin();

for ( ; i != v.end(); ++i ) {
    if (*i > x && *i < y) break;
}
```

Použijte moderní C++ následujícím způsobem:

```cpp
for_each( begin(strings), end(strings), [](string& s) {
  // ...
} );

auto i = find_if( begin(v), end(v),  [=](int i) { return i > x && i < y; } );
```

### <a name="range-based-for-loops"></a>Na základě rozsahu smyček for

Rozsahový **pro** smyčky je funkcí C ++ 11, jazyk, nikoli algoritmů standardní knihovny C++. Ale to si zaslouží zmínku v této diskuzi o smyčkách. Založený na rozsahu **pro** smyčky jsou rozšíření **pro** – klíčové slovo a poskytují pohodlný a účinný způsob, jak psát smyčky, které iterují v rozsahu hodnot. Jsou předdefinované pro kontejnery standardní knihovny C++, řetězce a pole vycházející z rozsahu **pro** smyčky. Pokud chcete povolit tuto novou syntaxi iterace pro váš typ definovaný uživatelem, přidejte následující podporu:

- A `begin` metodu, která vrátí iterátor na začátek struktury a `end` metodu, která vrátí iterátor na konec struktury.

- Podpora v iterátoru pro tyto metody: **operátor**<strong>\*</strong>, **operátor! =**, a **operator ++** (verze předpony).

Tyto metody mohou být členy nebo samostatné funkce.

## <a name="random-numbers"></a>Náhodná čísla

Není žádný tajný klíč, který staré CRT `rand()` funkce má mnoho vad, které mají byla Dlouze prodiskutovány komunitou C++. V moderním jazyce C++ nemusíte řešit tyto nedostatky – nemusíte vytvářet vlastní rovnoměrně distribuovaný generátor náhodných čísel, ani – protože nástroje pro rychlé a snadné vytváření jsou k dispozici ve standardní knihovně jazyka C++, jak je znázorněno v [ \<náhodné >](../standard-library/random.md).

## <a name="see-also"></a>Viz také:

[C++ vás vítá zpět (moderní verze jazyka C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)<br/>
