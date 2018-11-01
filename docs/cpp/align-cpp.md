---
title: align (C++)
ms.date: 11/04/2016
f1_keywords:
- align_cpp
helpviewer_keywords:
- align __declspec keyword
- __declspec keyword [C++], align
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
ms.openlocfilehash: f5353354a334f6ee597bca3e49dfa2b4f98a0005
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440440"
---
# <a name="align-c"></a>align (C++)

V sadě Visual Studio 2015 a novější, použijte standard C ++ 11 `alignas` specifikátor zarovnání ovládacího prvku. Další informace najdete v tématu [zarovnání](../cpp/alignment-cpp-declarations.md).

**Specifické pro Microsoft**

Použití `__declspec(align(#))` pro přesné řízení zarovnání dat definované uživatelem (například statické přidělení nebo automatická datová funkce).

## <a name="syntax"></a>Syntaxe

> **__declspec (zarovnání (** *#* **))** *deklarátorů*

## <a name="remarks"></a>Poznámky

Psaní aplikací, které používají nejnovější instrukce procesoru zavádí některá nová omezení a problémy. Mnoho nových pokynů zejména vyžaduje, že data musí být zarovnány na hranice 16 bajtů. Kromě toho přizpůsobením často používaných dat velikosti řádku mezipaměti konkrétního procesoru zvýšit výkon mezipaměti. Například pokud definujete strukturu, jejíž velikost je menší než 32 bajtů, můžete ji zarovnat na 32 bajtů. abyste měli jistotu, že objekty tohoto typu struktury efektivně ukládány.

\# je hodnota zarovnání. Platná zadání jsou celá čísla pro mocniny dvou od 1 do 8 192 (bajty), jako je například 2, 4, 8, 16, 32 nebo 64. `declarator` je údaj, který deklarujete jako zarovnaný.

Informace o tom, jak vrátit hodnotu typu `size_t` , který je požadavek zarovnání typu naleznete v tématu [__alignof](../cpp/alignof-operator.md). Informace o tom, jak deklarace nezarovnaných ukazatelů při cílení na 64bitové procesory, naleznete v tématu [__unaligned](../cpp/unaligned.md).

Můžete použít `__declspec(align(#))` při definování **struktura**, **sjednocení**, nebo **třída**, nebo pokud deklarujete proměnnou.

Kompilátor nepodporuje zaručit ani pokus o zachovávají atribut zarovnání dat během kopírování nebo data operace transformace. Například [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) můžete zkopírovat struktura deklarována s `__declspec(align(#))` do libovolného umístění. Všimněte si, že běžný alokátorů – například [malloc](../c-runtime-library/reference/malloc.md), C++ [operátor new](new-operator-cpp.md)a alokátory Win32 – vrátí paměť není dostatečně zarovnáno obvykle pro `__declspec(align(#))` nebo poli struktury. Chcete-li zaručit, že cíl kopírování nebo data operace transformace je správně zarovnán, použijte [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md), nebo napište vlastní Alokátor.

Nelze určit zarovnání pro parametry funkce. Data, která má atribut zarovnání je předán podle hodnoty v zásobníku, jeho zarovnání je řízeno konvence volání. Pokud zarovnání dat je důležité ve volané funkci, zkopírujte do správně zarovnané paměti před použitím parametru.

Bez `__declspec(align(#))`, kompilátor obecně Zarovná data na přirozené hranice v závislosti na cílový procesor a množství dat, až 4bajtových hranicích na 32bitové procesory a hranice 8 bajtů na 64bitové procesory. Data v třídách nebo strukturách jsou zarovnána v dané třídy nebo struktury alespoň na jejich přirozené zarovnání a aktuální nastavení balení (z #pragma `pack` nebo `/Zp` – možnost kompilátoru).

Tento příklad ukazuje použití `__declspec(align(#))`:

```cpp
__declspec(align(32)) struct Str1{
   int a, b, c, d, e;
};
```

Tento typ má nyní atribut zarovnání 32 bajtů. To znamená, že všechny instance statické a automatické spuštění na hranici 32 bajtů. Další typy struktur deklarované pomocí tohoto typu jako člen zachovávají atribut zarovnání tohoto typu, to znamená, že všechny struktury s `Str1` element má atribut zarovnání alespoň 32.

Všimněte si, že `sizeof(struct Str1)` je roven 32. Z toho vyplývá, že pokud je vytvořeno pole objektů Str1 a základ pole je 32 bajtů zarovnána, každý člen pole se také zarovnána na 32 bajtů. Chcete-li vytvořit pole, jehož základ je správně zarovnán v dynamické paměti, použijte [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md), nebo napište vlastní Alokátor.

`sizeof` Hodnotu pro libovolnou strukturu posunu posledního člena plus velikost tohoto člena, zaokrouhlená na nejbližší násobek největší hodnota člena zarovnání nebo hodnoty zarovnání celé struktury, která je větší.

Kompilátor používá pro zarovnání struktury tato pravidla:

- Pokud nejsou přepsány s `__declspec(align(#))`, zarovnání skalární struktury člena je minimální velikost a aktuální balení.

- Pokud nejsou přepsány s `__declspec(align(#))`, zarovnání struktury člena je maximum samostatného zarovnání jeho členů.

- Člen struktury je umístěn na posunu od začátku své nadřazené struktury, což je nejmenší násobek jeho zarovnání větší než nebo rovný posunu konce předchozího členu.

- Velikost struktury je nejmenší násobek jeho zarovnání větší než nebo rovný posunu konce jeho posledního člena.

`__declspec(align(#))` může pouze zvýšit omezení zarovnání.

Další informace naleznete v tématu:

- [Příklady zarovnání](#vclrfalignexamples)

- [Definování nových typů pomocí __declspec(align(#))](#vclrf_declspecaligntypedef)

- [Zarovnávání dat v místním úložišti vláken](#vclrfthreadlocalstorageallocation)

- [Jak align spolupracuje s balením dat](#vclrfhowalignworkswithdatapacking)

- [Příklady zarovnání struktur](../build/examples-of-structure-alignment.md) (x64 konkrétní)

##  <a name="vclrfalignexamples"></a> Příklady zarovnání

Následující příklady ukazují jak `__declspec(align(#))` ovlivňuje velikost a zarovnání datových struktur. V příkladech se předpokládají následující definice:

```cpp
#define CACHE_LINE  32
#define CACHE_ALIGN __declspec(align(CACHE_LINE))
```

V tomto příkladu `S1` struktura je definována pomocí `__declspec(align(32))`. Všechny výskyty `S1` pro definici proměnné nebo v jiném typu deklarace jsou zarovnána na 32 bajtů. `sizeof(struct S1)` Vrátí 32 a `S1` má 16 bajtů odsazení následujících po 16 bajtech potřebných k uložení čtyř celých čísel. Každý **int** člen vyžaduje 4bajtové zarovnání, ale zarovnání struktury samotné je deklarováno jako 32. Takže celkové zarovnání je 32.

```cpp
struct CACHE_ALIGN S1 { // cache align all instances of S1
   int a, b, c, d;
};
struct S1 s1;   // s1 is 32-byte cache aligned
```

V tomto příkladu `sizeof(struct S2)` vrátí 16, což je přesně součet velikostí členů, protože se jedná násobek největšího požadavku zarovnání (násobek 8).

```cpp
__declspec(align(8)) struct S2 {
   int a, b, c, d;
};
```

V následujícím příkladu `sizeof(struct S3)` vrátí hodnotu 64.

```cpp
struct S3 {
   struct S1 s1;   // S3 inherits cache alignment requirement
                  // from S1 declaration
   int a;         // a is now cache aligned because of s1
                  // 28 bytes of trailing padding
};
```

V tomto příkladu, Všimněte si, že `a` zarovnání jeho přírodního typu, v tomto případě 4 bajty. Ale `S1` musí být zarovnaný na 32 bajtů. Dvacet osm bajtů odsazení následuje `a`tak, aby `s1` začínala na posunu 32. `S4` poté dědí požadavky na zarovnání `S1`, protože se jedná o největší požadavek zarovnání ve struktuře. `sizeof(struct S4)` Vrátí hodnotu 64.

```cpp
struct S4 {
   int a;
   // 28 bytes padding
    struct S1 s1;      // S4 inherits cache alignment requirement of S1
};
```

Následující tři deklarace proměnných také používají `__declspec(align(#))`. V obou případech musí být proměnná zarovnána na 32 bajtů. V případě pole je základní adresa pole, nikoli každý člen pole zarovnána na 32 bajtů. `sizeof` Hodnotu pro každého člena pole neovlivní při použití `__declspec(align(#))`.

```cpp
CACHE_ALIGN int i;
CACHE_ALIGN int array[128];
CACHE_ALIGN struct s2 s;
```

Chcete-li zarovnat pole každého člena, byste měli použít kód takovou situaci:

```cpp
typedef CACHE_ALIGN struct { int a; } S5;
S5 array[10];
```

V tomto příkladu Všimněte si, že zarovnání samotné struktury a zarovnání prvního prvku mají stejný účinek:

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

`S6` a `S7` mají stejné zarovnání, rozdělení a charakteristiky velikostí.

V tomto příkladu zarovnání počáteční adresy a, b, c a d jsou 4, 1, 4 a 1, v uvedeném pořadí.

```cpp
void fn() {
   int a;
   char b;
   long c;
   char d[10]
}
```

Zarovnání, když je paměť přidělena v haldě, závisí na která funkce přidělení bude volána.  Například, pokud používáte `malloc`, výsledek závisí na velikosti operandu. Pokud *arg* > = 8, je paměť vrácena zarovnán na 8 bajtů. Pokud *arg* < 8, zarovnání paměti vrátí se o první mocninu 2 menší než *arg*. Například pokud používáte malloc(7), zarovnání je 4 bajty.

##  <a name="vclrf_declspecaligntypedef"></a> Definování nových typů pomocí __declspec(align(#))

Můžete definovat typ s charakteristickým zarovnáním.

Například můžete definovat `struct` s hodnotou zarovnání takto:

```cpp
struct aType {int a; int b;};
typedef __declspec(align(32)) struct aType bType;
```

Nyní `aType` a `bType` jsou stejné velikosti (8 bajtů), ale proměnné typu `bType` jsou zarovnána na 32 bajtů.

##  <a name="vclrfthreadlocalstorageallocation"></a> Zarovnávání dat v místním úložišti vláken

Statické úložiště thread local (TLS) vytvořené pomocí `__declspec(thread)` atribut a vložit ho do části TLS v obraze umožňuje zarovnání úplně stejně jako normální statická data. Pokud chcete vytvořit data protokolu TLS, operační systém přiděluje paměť velikosti sekce TLS a respektuje atributu zarovnání sekce TLS.

Tento příklad ukazuje různé způsoby umístění zarovnaných dat do úložiště thread local.

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

##  <a name="vclrfhowalignworkswithdatapacking"></a> Jak align spolupracuje s balením dat

`/Zp` – Možnost kompilátoru a `pack` – Direktiva pragma mají vliv na dodací údaje pro členy struktury a sjednocení. Tento příklad ukazuje, jak `/Zp` a `__declspec(align(#))` spolupracují:

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

Následující tabulka uvádí posun pro každého člena podle různých `/Zp` (nebo #pragma `pack`) hodnotami, zobrazení jejich interakce.

|Proměnná|/Zp1|/Zp2|/Zp4|/ Zp8|
|--------------|-----------|-----------|-----------|-----------|
|a|0|0|0|0|
|b|1|2|2|2|
|c|3|4|4|8|
|d|32|32|32|32|
|e|40|40|40|40|
|f|41|42|44|48|
|sizeof (S)|64|64|64|64|

Další informace najdete v tématu [/Zp (zarovnání členů struktury)](../build/reference/zp-struct-member-alignment.md).

Posun objektu je založeno na posunu na předchozí objekt a aktuální nastavení balení, pokud nemá objekt `__declspec(align(#))` atribut, v takovém případě je zarovnání založeno na posunu na předchozí objekt a `__declspec(align(#))` hodnotu objektu.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Přehled konvencí ARM ABI](../build/overview-of-arm-abi-conventions.md)<br/>
[Přehled konvencí volání v prostředí x64](../build/overview-of-x64-calling-conventions.md)