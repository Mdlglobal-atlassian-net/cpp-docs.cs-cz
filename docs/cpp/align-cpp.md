---
title: align (C++)
ms.date: 12/17/2018
f1_keywords:
- align_cpp
helpviewer_keywords:
- align __declspec keyword
- __declspec keyword [C++], align
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
ms.openlocfilehash: 227053fbfa4190dc6227ba7096a7c76aef30bb54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181548"
---
# <a name="align-c"></a>align (C++)

V aplikaci Visual Studio 2015 nebo novější použijte k řízení zarovnání specifikátor Standard `alignas` jazyka C++ 11. Další informace najdete v tématu [Zarovnání](../cpp/alignment-cpp-declarations.md).

**Specifické pro společnost Microsoft**

Použijte `__declspec(align(#))` k přesnému řízení zarovnání uživatelsky definovaných dat (například statických přidělení nebo automatických dat ve funkci).

## <a name="syntax"></a>Syntaxe

> **__declspec (align (** *#* **))** *deklarátor*

## <a name="remarks"></a>Poznámky

Zápis aplikací, které používají nejnovější instrukce procesoru, zavádí některá nová omezení a problémy. Konkrétně mnoho nových pokynů vyžaduje, aby data byla zarovnaná na hranice 16 bajtů. Díky zarovnání často používaných dat na velikost řádku mezipaměti pro určitý procesor můžete navíc zlepšit výkon mezipaměti. Například pokud definujete strukturu, jejíž velikost je menší než 32 bajtů, může být vhodné ji zarovnat na 32 bajtů, aby bylo zajištěno, že objekty tohoto typu struktury budou efektivně uloženy v mezipaměti.

\# je hodnota zarovnání. Platné položky jsou celá čísla mocnin dvou než 1 až 8192 (bajtů), například 2, 4, 8, 16, 32 nebo 64. `declarator` jsou data, která deklarujete jako zarovnaná.

Informace o tom, jak vrátit hodnotu typu `size_t`, který je požadavkem na zarovnání tohoto typu, naleznete v tématu [__alignof](../cpp/alignof-operator.md). Informace o tom, jak deklarovat nezarovnané ukazatele při cílení na 64 procesory, naleznete v tématu [__unaligned](../cpp/unaligned.md).

Můžete použít `__declspec(align(#))` při definování **struktury**, **sjednocení**nebo **třídy**nebo při deklaraci proměnné.

Kompilátor nezaručuje ani nepokusí zachovat atribut zarovnání dat během operace kopírování nebo transformace dat. Například [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) může zkopírovat strukturu deklarovanou s `__declspec(align(#))` do libovolného umístění. Mějte na [paměti, že](../c-runtime-library/reference/malloc.md)běžná přidělování – například "zajistění, C++ [operátor New](new-operator-cpp.md)a přidělování Win32" – vracejí paměť, která není obvykle dostatečně zarovnaná pro `__declspec(align(#))` struktury nebo pole struktur. Aby bylo zaručeno, že cíl operace kopírování nebo transformace dat je správně zarovnán, použijte [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)nebo napište vlastní Alokátor.

Pro parametry funkce nelze zadat zarovnání. Když jsou data s atributem zarovnání předána hodnotou v zásobníku, je jeho zarovnání řízeno konvencí volání. Pokud je u volané funkce důležité zarovnání dat, před použitím zkopírujte parametr do správně zarovnaných paměti.

Bez `__declspec(align(#))`kompilátor obecně zarovnává data v přirozených hranicích na základě cílového procesoru a velikosti dat, až po 4 bajtech na 32 procesorech a na 64 hranicích pro procesory s 8 bajty. Data v třídách nebo strukturách jsou zarovnána ve třídě nebo struktuře s minimálním jeho přirozeným zarovnáním a aktuálním nastavením balení (z #pragma `pack` nebo v možnosti kompilátoru `/Zp`).

Tento příklad ukazuje použití `__declspec(align(#))`:

```cpp
__declspec(align(32)) struct Str1{
   int a, b, c, d, e;
};
```

Tento typ má teď atribut zarovnání 32 bajtů. To znamená, že všechny statické a automatické instance začínají na hranici 32 bajtů. Další typy struktury deklarované s tímto typem jako člen zachovávají atribut zarovnání tohoto typu, to znamená, že jakákoli struktura s `Str1` jako element má atribut zarovnání aspoň 32.

Všimněte si, že `sizeof(struct Str1)` se rovná 32. To znamená, že pokud je vytvořeno pole objektů str1 a základ pole je 32-Byte, je každý člen pole také zarovnán 32-Byte. Chcete-li vytvořit pole, jehož základem je správně zarovnána v dynamické paměti, použijte [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)nebo napište vlastní Alokátor.

Hodnota `sizeof` pro jakoukoli strukturu je posunem finálního členu a jeho velikost, zaokrouhluje se na nejbližší násobek největší hodnoty zarovnání členů nebo hodnota zarovnání celé struktury, podle toho, co je větší.

Kompilátor používá tato pravidla pro zarovnání struktury:

- Pokud není přepsána v `__declspec(align(#))`, zarovnání člena skalární struktury je minimální velikost a aktuální balení.

- Pokud není přepsáno pomocí `__declspec(align(#))`, zarovnání struktury je maximální hodnota individuálního zarovnání jeho členů.

- Člen struktury je umístěn posun od začátku své nadřazené struktury, což je nejmenší násobek jeho zarovnání větší než nebo rovno posunu konce předchozího člena.

- Velikost struktury je nejmenší násobek jeho zarovnání větší než nebo rovno posunu konce posledního člena.

`__declspec(align(#))` může zvýšit jenom omezení zarovnání.

Další informace naleznete v tématu:

- [Příklady zarovnání](#vclrfalignexamples)

- [Definování nových typů pomocí __declspec (align (#))](#vclrf_declspecaligntypedef)

- [Zarovnávání dat v místním úložišti vláken](#vclrfthreadlocalstorageallocation)

- [Jak funguje funkce align s balíčkem data](#vclrfhowalignworkswithdatapacking)

- [Příklady zarovnání struktury](../build/x64-software-conventions.md#examples-of-structure-alignment) (specifické pro procesory x64)

## <a name="align-examples"></a><a name="vclrfalignexamples"></a>Příklady zarovnání

Následující příklady ukazují, jak `__declspec(align(#))` ovlivňují velikost a zarovnání datových struktur. V příkladech se předpokládá následující definice:

```cpp
#define CACHE_LINE  32
#define CACHE_ALIGN __declspec(align(CACHE_LINE))
```

V tomto příkladu je struktura `S1` definovaná pomocí `__declspec(align(32))`. Všechna použití `S1` pro definici proměnné nebo v jiných deklaracích typů jsou zarovnaná na 32 bajtů. `sizeof(struct S1)` vrátí 32 a `S1` má 16 bajtů odsazení po 16 bajtech potřebných k uložení čtyř celých čísel. Každý člen **int** vyžaduje zarovnání 4 bajty, ale zarovnání samotné struktury je deklarované jako 32. Proto celkové zarovnání je 32.

```cpp
struct CACHE_ALIGN S1 { // cache align all instances of S1
   int a, b, c, d;
};
struct S1 s1;   // s1 is 32-byte cache aligned
```

V tomto příkladu `sizeof(struct S2)` vrátí hodnotu 16, která je přesně součtem velikostí členů, protože to je násobek největšího požadavku zarovnání (násobek 8).

```cpp
__declspec(align(8)) struct S2 {
   int a, b, c, d;
};
```

V následujícím příkladu `sizeof(struct S3)` vrátí 64.

```cpp
struct S3 {
   struct S1 s1;   // S3 inherits cache alignment requirement
                  // from S1 declaration
   int a;         // a is now cache aligned because of s1
                  // 28 bytes of trailing padding
};
```

V tomto příkladu si všimněte, že `a` má zarovnání jeho přirozeného typu, v tomto případě 4 bajty. `S1` však musí být zarovnaná na 32 bajtů. 20 – osm bajtů odsazení podle `a`, aby `s1` začíná na posunu 32. `S4` pak zdědí požadavek na zarovnání `S1`, protože se jedná o největší požadavek na zarovnání ve struktuře. `sizeof(struct S4)` vrátí 64.

```cpp
struct S4 {
   int a;
   // 28 bytes padding
    struct S1 s1;      // S4 inherits cache alignment requirement of S1
};
```

Následující tři deklarace proměnných také používají `__declspec(align(#))`. V každém případě musí být proměnná zarovnaná na 32 bajtů. V případě pole je základní adresa pole, ne každý člen pole, zarovnaná 32 bajtů. Hodnota `sizeof` pro každého člena pole není ovlivněna při použití `__declspec(align(#))`.

```cpp
CACHE_ALIGN int i;
CACHE_ALIGN int array[128];
CACHE_ALIGN struct s2 s;
```

Pro zarovnávání jednotlivých členů pole by měl být použit kód, jako je třeba tento:

```cpp
typedef CACHE_ALIGN struct { int a; } S5;
S5 array[10];
```

V tomto příkladu si všimněte, že zarovnání samotné struktury a zarovnání prvního prvku mají stejný účinek:

```cpp
CACHE_ALIGN struct S6 {
   int a;
   int b;
};

struct S7 {
   CACHE_ALIGN int a;
               int b;
};
```

`S6` a `S7` mají stejné charakteristiky zarovnání, alokace a velikosti.

V tomto příkladu je zarovnání počátečních adres a, b, c a d v uvedeném pořadí 4, 1, 4 a 1.

```cpp
void fn() {
   int a;
   char b;
   long c;
   char d[10]
}
```

Zarovnání, pokud je paměť přidělena haldě, závisí na tom, která funkce přidělení je volána.  Například pokud použijete `malloc`, výsledek závisí na velikosti operandu. Pokud *arg* > = 8, vrácená paměť je 8 bajtů. Pokud *arg* < 8, je zarovnání vrácené paměti prvním mocninou 2 menší než *arg*. Například pokud použijete pole \ (7), zarovnání je 4 bajty.

## <a name="defining-new-types-with-__declspecalign"></a><a name="vclrf_declspecaligntypedef"></a>Definování nových typů pomocí __declspec (align (#))

Můžete definovat typ s charakteristikou zarovnání.

Například můžete definovat `struct` s hodnotou zarovnání tímto způsobem:

```cpp
struct aType {int a; int b;};
typedef __declspec(align(32)) struct aType bType;
```

Nyní jsou `aType` a `bType` stejné velikosti (8 bajtů), ale proměnné typu `bType` jsou zarovnané 32-Byte.

## <a name="aligning-data-in-thread-local-storage"></a><a name="vclrfthreadlocalstorageallocation"></a>Zarovnávání dat v místním úložišti vláken

Statické místní úložiště (TLS) vytvořené pomocí atributu `__declspec(thread)` a v části TLS v imagi funguje pro zarovnání přesně jako běžná statická data. Při vytváření dat TLS operační systém přiděluje paměť velikosti oddílu TLS a respektuje atribut zarovnání oddílu TLS.

Tento příklad ukazuje různé způsoby, jak umístit zarovnaná data do úložiště thread local.

```cpp
// put an aligned integer in TLS
__declspec(thread) __declspec(align(32)) int a;

// define an aligned structure and put a variable of the struct type
// into TLS
__declspec(thread) __declspec(align(32)) struct F1 { int a; int b; } a;

// create an aligned structure
struct CACHE_ALIGN S9 {
   int a;
   int b;
};
// put a variable of the structure type into TLS
__declspec(thread) struct S9 a;
```

## <a name="how-align-works-with-data-packing"></a><a name="vclrfhowalignworkswithdatapacking"></a>Jak funguje funkce align s balíčkem data

Možnost kompilátoru `/Zp` a direktiva pragma `pack` mají vliv na data balení pro členy struktury a sjednocení. Tento příklad ukazuje, jak `/Zp` a `__declspec(align(#))` spolupracují:

```cpp
struct S {
   char a;
   short b;
   double c;
   CACHE_ALIGN double d;
   char e;
   double f;
};
```

V následující tabulce je uveden posun každého člena v rámci různých hodnot `/Zp` (nebo #pragma `pack`), který ukazuje, jak se obě interakceují.

|Proměnná|/Zp1|/Zp2|/Zp4|/Zp8|
|--------------|-----------|-----------|-----------|-----------|
|a|0|0|0|0|
|b|1|2|2|2|
|c|3|4|4|8|
|d|32|32|32|32|
|e|40|40|40|40|
|f|41|42|44|48|
|sizeof (S)|64|64|64|64|

Další informace naleznete v tématu [/zp (zarovnání členů struktury)](../build/reference/zp-struct-member-alignment.md).

Posun objektu je založen na posunu předchozího objektu a aktuálního nastavení balení, pokud objekt nemá atribut `__declspec(align(#))`, v takovém případě je zarovnání založeno na posunu předchozího objektu a `__declspec(align(#))` hodnotě objektu.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[Přehled konvencí ARM ABI](../build/overview-of-arm-abi-conventions.md)<br/>
[x64 – softwarové konvence](../build/x64-software-conventions.md)
