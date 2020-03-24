---
title: Číselné, logické a literály ukazatele (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- literals, C++
- constants, literals
- literals [C++]
ms.assetid: 17c09fc3-3ad7-47e2-8b48-ba8ae994edc8
ms.openlocfilehash: 21685af5fc4f2dcf042698e054430e50531163b7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177739"
---
# <a name="numeric-boolean-and-pointer-literals"></a>Číselné, logické a literály ukazatele

Literál je prvek programu, který přímo představuje hodnotu. Tento článek se zabývá literály typu celé číslo, plovoucí desetinná čárka, logická hodnota a ukazatel. Informace o řetězcových a znakových literálech naleznete v tématu [řetězcové a znakovéC++literály ()](../cpp/string-and-character-literals-cpp.md). Můžete také definovat vlastní literály založené na kterékoli z těchto kategorií; Další informace najdete v tématu [uživatelsky definované literályC++()](../cpp/user-defined-literals-cpp.md) .

. Můžete použít literály v mnoha kontextech, ale nejčastěji inicializovat pojmenované proměnné a předat argumenty funkcím:

```cpp
const int answer = 42; // integer literal
double d = sin(108.87);     //floating point literal passed to sin function
bool b = true;              // boolean literal
MyClass* mc = nullptr;      // pointer literal
```

V některých případech je důležité sdělit kompilátoru, jak interpretovat literál nebo jaký konkrétní typ k němu dát. Provedete to tak, že do literálu připojíte předpony nebo přípony. Například předpona 0x říká kompilátoru, aby interpretoval číslo, které následuje jako šestnáctková hodnota, například 0x35. Přípona ULL říká kompilátoru, aby považovala hodnotu jako typ **long long typu bez znaménka** , jako v 5894345ULL. Úplný seznam předpon a přípon pro každý typ literálu najdete v následujících oddílech.

## <a name="integer-literals"></a>Celočíselné literály

Celočíselné literály začínají číslicí a nemají žádné zlomkové části ani exponenty. Můžete zadat celočíselné literály v desítkové, osmičkové nebo šestnáctkové formě. Je možné určit typy se znaménkem nebo bez znaménka, dlouhé nebo krátké.

Pokud není přítomna žádná předpona nebo přípona, kompilátor poskytne celočíselnou hodnotu literálu **int** (32 bitů), pokud se hodnota přizpůsobí, jinak poskytne typ **long long** (64 bitů).

Chcete-li zadat desítkový celočíselný literál, spusťte specifikaci s nenulovou číslicí. Příklad:

```cpp
int i = 157;   // Decimal literal
int j = 0198;       // Not a decimal number; erroneous octal literal
int k = 0365;       // Leading zero specifies octal literal, not decimal
int m = 36'000'000  // digit separators make large values more readable
int
```

Chcete-li zadat osmičkový celočíselný literál, zahajte specifikaci hodnotou 0, následovanou posloupností číslic v rozsahu 0 až 7. Číslice 8 a 9 jsou chyby při zadávání osmičkového literálu. Příklad:

```cpp
int i = 0377;   // Octal literal
int j = 0397;        // Error: 9 is not an octal digit
```

Chcete-li určit hexadecimální celočíselný literál, zahajte specifikaci pomocí `0x` nebo `0X` (nezáleží na velikosti "x") následovaný posloupností číslic v rozsahu `0` až `9` a `a` (nebo `A`) až `f` (nebo `F`). Šestnáctkové číslice `a` (nebo `A`) až `f` (nebo `F`) představují hodnoty v rozsahu 10 až 15. Příklad:

```cpp
int i = 0x3fff;   // Hexadecimal literal
int j = 0X3FFF;        // Equal to i
```

Chcete-li zadat typ bez znaménka, použijte buď příponu `u` nebo `U`. Chcete-li zadat dlouhý typ, použijte buď příponu `l` nebo `L`. Chcete-li určit 64 integrálový typ, použijte příponu LL nebo LL. Přípona I64 je stále podporovaná, ale měla by se vyhýbat, protože je specifická pro společnost Microsoft a není přenosná. Příklad:

```cpp
unsigned val_1 = 328u;             // Unsigned value
long val_2 = 0x7FFFFFL;                 // Long value specified
                                        //  as hex literal
unsigned long val_3 = 0776745ul;        // Unsigned long value
auto val_4 = 108LL;                           // signed long long
auto val_4 = 0x8000000000000000ULL << 16;     // unsigned long long
```

**Oddělovače číslic**: pomocí znaku jednoduché uvozovky (apostrof) můžete oddělit hodnoty na větší čísla, aby je lidé snadněji četli. Oddělovače nemají žádný vliv na kompilaci.

```cpp
long long i = 24'847'458'121
```

## <a name="floating-point-literals"></a>Literály s plovoucí desetinnou čárkou

Literály s plovoucí desetinnou čárkou určují hodnoty, které musí obsahovat zlomkovou část. Tyto hodnoty obsahují desetinná místa ( **.** ) a mohou obsahovat exponenty.

Literály s plovoucí desetinnou čárkou mají "mantisu", která určuje hodnotu čísla, exponent, který určuje velikost čísla a volitelnou příponu, která určuje typ literálu. Mantisa je zadána jako posloupnost číslic následovaných čárkou a je následována řadou číslic představující zlomkovou část čísla. Příklad:

```cpp
18.46
38.
```

Exponent, pokud je k dispozici, určuje velikost čísla jako mocninu 10, jak je znázorněno v následujícím příkladu:

```cpp
18.46e0      // 18.46
18.46e1           // 184.6
```

Exponent lze zadat pomocí `e` nebo `E`, která má stejný význam následovaný volitelným znaménkem (+ nebo-) a posloupností číslic.  Je-li exponent použit, koncová desetinná čárka není nutná u celých čísel, jako je `18E0`.

Literály s plovoucí desetinnou čárkou jsou výchozí pro typ **Double**. Pomocí přípon `f` nebo `l` (nebo `F` nebo `L` – přípona nerozlišuje malá a velká písmena), literál může být zadán jako **float** nebo **Long Double**v uvedeném pořadí.

I když má **dlouhá dvojitá** a **dvojnásobná** reprezentace stejnou reprezentaci, není stejný typ. Například je možné mít přetížené funkce jako

```cpp
void func( double );
```

a

```cpp
void func( long double );
```

## <a name="boolean-literals"></a>Logické literály

Logické literály jsou **true** a **false**.

## <a name="pointer-literal-c11"></a>Literál ukazatele (C++ 11)

C++zavádí literál [nullptr](../cpp/nullptr.md) pro určení ukazatele s nulovým inicializací. V přenositelném kódu by měla být použita hodnota **nullptr** namísto celočíselného typu nula nebo makra, jako je například null.

## <a name="binary-literals-c14"></a>Binární literály (C++ 14)

Binární literál lze určit pomocí `0B` nebo předpony `0b` následovaný sekvencí 1 a 0:

```cpp
auto x = 0B001101 ; // int
auto y = 0b000001 ; // int
```

## <a name="avoid-using-literals-as-magic-constants"></a>Vyhněte se použití literálů jako "Magic konstant".

Můžete použít literály přímo ve výrazech a příkazech, i když není vždy dobrým zvykem programování:

```cpp
if (num < 100)
    return "Success";
```

V předchozím příkladu může být lepší použít pojmenovanou konstantu, která vyjadřuje jasný význam, například "MAXIMUM_ERROR_THRESHOLD". A Pokud koncoví uživatelé uvidí návratovou hodnotu "úspěch", může být lepší použít pojmenovanou řetězcovou konstantu, která může být uložena v jednom umístění v souboru, ze kterého může být lokalizována do jiných jazyků. Použití pojmenovaných konstant pomáhá ostatním uživatelům a pochopit záměr kódu.

## <a name="see-also"></a>Viz také

[Lexikální konvence](../cpp/lexical-conventions.md)<br/>
[C++Řetězcové literály](../cpp/string-and-character-literals-cpp.md)<br/>
[C++Uživatelsky definované literály](../cpp/user-defined-literals-cpp.md)
