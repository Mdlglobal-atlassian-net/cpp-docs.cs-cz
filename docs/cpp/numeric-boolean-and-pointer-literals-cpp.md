---
title: Číselné literály, logické a literály typu ukazatele (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- literals, C++
- constants, literals
- literals [C++]
ms.assetid: 17c09fc3-3ad7-47e2-8b48-ba8ae994edc8
ms.openlocfilehash: f263e9a2ed357cdc80ec29fc5d1b6d58c9e093e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545792"
---
# <a name="numeric-boolean-and-pointer-literals--c"></a>Číselné literály, logické a literály typu ukazatele (C++)

Literál je prvek programu, který představuje hodnotu přímo. Tento článek se týká literály celočíselného typu s plovoucí desetinnou čárkou, logické a ukazatele. Informace o literálech řetězců a znaků naleznete v tématu [řetězcové a znakové literály (C++)](../cpp/string-and-character-literals-cpp.md). Můžete také definovat vlastní literály založené na kteroukoli z těchto kategorií; Další informace najdete v části [uživatelem definované literály (C++)](../cpp/user-defined-literals-cpp.md)

. Můžete literály v mnoha kontextech, ale většina běžně inicializovat pojmenované proměnné a předání argumentů funkce:

```cpp
const int answer = 42; // integer literal
double d = sin(108.87);     //floating point literal passed to sin function
bool b = true;              // boolean literal
MyClass* mc = nullptr;      // pointer literal
```

Někdy je důležité, abyste kompilátoru literálem interpretace nebo jaké konkrétní typ, abyste k němu. To provedete přidáním předpony nebo přípony literálu. Například předponu 0 x instruuje kompilátor, aby čísla, která ji následuje jako šestnáctkovou hodnotu, například 0x35 interpretovat. Přípona ULL instruuje kompilátor, aby považovat za hodnotu **unsigned long long.** typ, stejně jako v 5894345ULL. Podívejte se v následujících částech úplný seznam předpon a přípon, pro každý typ literálu.

## <a name="syntax"></a>Syntaxe

## <a name="integer-literals"></a>Literály celých čísel

Literály celých čísel začínají číslicí a mít žádné zlomkové části nebo exponenty. Literály celých čísel můžete zadat v podobě desítkové, osmičkové nebo šestnáctkové. Je možné určit typy se znaménkem nebo bez znaménka, dlouhé nebo krátké.

Pokud je k dispozici žádná předpona nebo přípona, kompilátor vám poskytne typem celočíselný literál **int** (32bitová verze), pokud se hodnota, jinak poskytne to typ **long long** (64 bitů).

K určení desetinné celočíselný literál, je nutné začněte specifikaci nenulovou číslicí. Příklad:

```cpp
int i = 157;   // Decimal literal
int j = 0198;       // Not a decimal number; erroneous octal literal
int k = 0365;       // Leading zero specifies octal literal, not decimal
int m = 36'000'000  // digit separators make large values more readable
int
```

K určení osmičkové celočíselný literál, je nutné začněte specifikaci s 0, následovanou posloupností číslic v rozsahu 0 až 7. Číslice 8 a 9 jsou chyby v určení osmičkové literální. Příklad:

```cpp
int i = 0377;   // Octal literal
int j = 0397;        // Error: 9 is not an octal digit
```

Chcete-li určit šestnáctkové celočíselný literál, je nutné začít specifikaci s `0x` nebo `0X` (případ "x" nezáleží), následované posloupností číslic v rozsahu `0` prostřednictvím `9` a `a` (nebo `A`) prostřednictvím `f` (nebo `F`). Šestnáctkové číslice `a` (nebo `A`) až `f` (nebo `F`) představují hodnoty v rozsahu 10 až 15. Příklad:

```cpp
int i = 0x3fff;   // Hexadecimal literal
int j = 0X3FFF;        // Equal to i
```

Chcete-li určit typ bez znaménka, použijte buď `u` nebo `U` příponu. Chcete-li určit dlouhý typ, použijte buď `l` nebo `L` příponu. Chcete-li určit 64bitového celočíselného typu, použijte LL nebo příponu ll. Přípona i64 stále podporovány, ale mělo by se vyhnout, protože je specifické pro společnost Microsoft a není přenosný. Příklad:

```cpp
unsigned val_1 = 328u;             // Unsigned value
long val_2 = 0x7FFFFFL;                 // Long value specified
                                        //  as hex literal
unsigned long val_3 = 0776745ul;        // Unsigned long value
auto val_4 = 108LL;                           // signed long long
auto val_4 = 0x8000000000000000ULL << 16;     // unsigned long long
```

**Oddělovače číslic:**: znak uvozovek (apostrof) můžete použít k oddělení místo hodnoty ve větší čísla, aby se daly snadněji číst člověka. Oddělovače nemají žádný vliv při kompilaci.

```cpp
long long i = 24'847'458'121
```

## <a name="floating-point-literals"></a>Literály plovoucího bodu

Literály s plovoucí desetinnou čárkou určit hodnoty, které musí mít desetinnou část. Tyto hodnoty obsahují desetinné čárky (**.**) a mohou obsahovat exponenty.

S plovoucí desetinnou čárkou literály mají "mantisu," Určuje hodnotu čísla, "exponentu" Určuje velikost čísla a volitelnou příponu, která určuje typ je literál. Mantisa je zadána jako posloupnost číslic následovaných čárkou a je následována řadou číslic představující zlomkovou část čísla. Příklad:

```cpp
18.46
38.
```

Exponent, pokud je k dispozici, určuje velikost čísla jako mocninu 10, jak je znázorněno v následujícím příkladu:

```cpp
18.46e0      // 18.46
18.46e1           // 184.6
```

Exponent může být určen pomocí `e` nebo `E`, které mají stejný význam, následovaný nepovinným znaménkem (+ nebo -) a posloupností číslic.  Je-li exponent použit, koncová desetinná čárka není nutná u celých čísel, jako je `18E0`.

Literály s plovoucí desetinnou čárkou ve výchozím stavu typem **double**. Pomocí přípon `f` nebo `l` (nebo `F` nebo `L` – přípona nerozlišuje velká a malá písmena), literálu se dá nastavit jako **float** nebo **long double**, v uvedeném pořadí.

I když **long double** a **double** stejnou reprezentaci, nejsou stejného typu. Například je možné mít přetížené funkce jako

```cpp
void func( double );
```

and

```cpp
void func( long double );
```

## <a name="boolean-literals"></a>Logické hodnoty literálu

Logické hodnoty literálu jsou **true** a **false**.

## <a name="pointer-literal-c11"></a>Literál ukazatele (C ++ 11)

Zavádí C++ [nullptr](../cpp/nullptr.md) literálu pro určení ukazatele inicializována nulou. V přenositelném kódu **nullptr** by měla sloužit místo nula integrálového typu nebo makra, jako je NULL.

## <a name="binary-literals-c14"></a>Binární literály (C ++ 14)

Binární literál je možné zadat tak použití `0B` nebo `0b` předponu, za nímž následuje posloupnost 1 a uživatele 0:

```cpp
auto x = 0B001101 ; // int
auto y = 0b000001 ; // int
```

## <a name="avoid-using-literals-as-magic-constants"></a>Nepoužívejte literály jako "magic konstanty"

I když to není vždy programování je dobrým zvykem, můžete použít literály přímo v výrazy a příkazy:

```cpp
if (num < 100)
    return "Success";
```

V předchozím příkladu může být vhodnější použít pojmenované konstanty, která přenáší jasný význam, například "MAXIMUM_ERROR_THRESHOLD". A pokud vrácená hodnota, která se zobrazuje "Success" tak, že koncoví uživatelé, pak může být vhodnější použít pojmenované řetězcová konstanta, která mohou být uloženy v jednom umístění v souboru z kde může být lokalizována do jiných jazyků. Použití pojmenované konstanty pomáhá ostatním také sobě a porozumění záměru kódu.

## <a name="see-also"></a>Viz také:

[Lexikální konvence](../cpp/lexical-conventions.md)<br/>
[Textové literály jazyka C++](../cpp/string-and-character-literals-cpp.md)<br/>
[Uživateli definované literály jazyka C++](../cpp/user-defined-literals-cpp.md)