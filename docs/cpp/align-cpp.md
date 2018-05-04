---
title: align (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- align_cpp
dev_langs:
- C++
helpviewer_keywords:
- align __declspec keyword
- __declspec keyword [C++], align
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae88262724dfec5702e2769eb10e076502c09342
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="align-c"></a>align (C++)

V sadě Visual Studio 2015 a novější, použijte C ++ 11 standard `alignas` specifikátor pro zarovnání ovládacího prvku. Další informace najdete v tématu [zarovnání](../cpp/alignment-cpp-declarations.md).

**Konkrétní Microsoft**

Použití `__declspec(align(#))` přesně řídit zarovnání uživatelem definované datové (například statických přidělených nebo dat ve funkci).

## <a name="syntax"></a>Syntaxe

> **__declspec (align (** *#* **))** *deklarátor*  

## <a name="remarks"></a>Poznámky

Zápis aplikací, které používají nejnovější pokynů procesoru zavádí některé nové omezení a problémy. Mnoho nové pokyny klást, data musí být zarovnána na 16 bajtů hranice. Kromě toho slaďte často používaných dat do mezipaměti velikost řádku specifické procesory, můžete zlepšit výkon mezipaměti. Například pokud definujete struktura, jejíž aktuální velikost je menší než 32 bajtů, můžete zarovnat na 32 bajtů, abyste měli jistotu, že objekty tohoto typu Struktura efektivně v mezipaměti.

\# je hodnota zarovnání. Platné položky jsou zajišťuje celé číslo od 1 do 8192 (v bajtech), jako jsou například 2, 4, 8, 16, 32 nebo 64 dva. `declarator` jsou data, která jsou deklarace jako zarovnána.

Informace o tom, jak vrátit hodnotu typu `size_t` , je požadavek na zarovnání typu, najdete v části [__alignof –](../cpp/alignof-operator.md). Informace o tom, jak deklarace nezarovnané ukazatelů, pokud je cílem 64bitovými procesory najdete v tématu [__unaligned](../cpp/unaligned.md).

Můžete použít `__declspec(align(#))` při definování `struct`, `union`, nebo `class`, nebo když je deklarovat proměnnou.

Kompilátor není zaručit nebo se pokuste o zachovat atribut zarovnání dat během operace transformace kopírování nebo data. Například [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) můžete zkopírovat struktury deklarovat s `__declspec(align(#))` do libovolného umístění. Všimněte si, že běžném provozu alokátorů – například [malloc –](../c-runtime-library/reference/malloc.md), C++ [new – operátor](new-operator-cpp.md)a alokátorů Win32 – vrátí paměti, která není dostatečně zarovnána obvykle pro `__declspec(align(#))` struktury nebo pole struktury. Chcete-li zaručit, že je správně zarovnán cíl operace transformace kopírování nebo data, použijte [_aligned_malloc –](../c-runtime-library/reference/aligned-malloc.md), nebo napište vlastní přidělení.

Nelze zadat zarovnání parametry funkce. Data, která má atribut zarovnání je předaná hodnota v zásobníku, jeho zarovnání je řízeno konvence volání. Pokud zarovnání dat je důležité v volaná funkce, zkopírujte do paměti, správně zarovnané před použitím parametru.

Bez `__declspec(align(#))`, kompilátor obecně Zarovná data na přirozené hranic na základě cílový procesor a velikost dat, až 4bajtový hranice u 32-bit procesorů a 8bajtový hranice na 64bitovými procesory. Data v třídy nebo struktury je zarovnán v třídu nebo strukturu alespoň jeho přirozené zarovnání a nastavení aktuální balení (z #pragma `pack` nebo **/Zp** – možnost kompilátoru).

Tento příklad ukazuje použití `__declspec(align(#))`:

```cpp
__declspec(align(32)) struct Str1{
   int a, b, c, d, e;
};
```

Tento typ má nyní atribut zarovnání 32 bajtů. To znamená, že všechny instance statické a automatického spuštění na hranici 32 bajtů. Struktura další typy deklarovat s tímto typem jako člen zachovat atribut zarovnání tento typ, tedy žádné struktury s `Str1` jako element má atribut zarovnání alespoň 32.

Všimněte si, že `sizeof(struct Str1)` je rovna 32. Z toho vyplývá, že pokud je pole objektů Str1 vytvořili, a základní pole je 32 bajtů zarovnán, každý člen pole je také zarovnán 32 bajtů. K vytvoření pole, jehož základní je správně zarovnán v dynamické paměti, použijte [_aligned_malloc –](../c-runtime-library/reference/aligned-malloc.md), nebo napište vlastní přidělení.

`sizeof` u všech struktura posun posledního člena plus velikost tohoto člena, zaokrouhlený nahoru na nejbližší násobek největší hodnotu zarovnání člen nebo hodnota zarovnání celou struktura, podle toho, která je větší.

Kompilátor používá pro zarovnání struktury tato pravidla:

- Pokud není přepsána s `__declspec(align(#))`, zarovnání struktury skalární člen je minimálně jeho velikost a aktuální okolních.

- Pokud není přepsána s `__declspec(align(#))`, zarovnání struktury je maximální počet jednotlivých zarovnání její členy.

- Struktura člen je umístěn na posun od začátku její nadřazená struktura, což je nejmenší násobkem její zarovnání větší než nebo rovna hodnotě Posun konci předchozího člena.

- Velikost strukturou je nejmenší násobkem její zarovnání větší než nebo rovna hodnotě posunutí konce jeho posledním členem.

`__declspec(align(#))` může se zvýšit pouze omezení zarovnání.

Další informace naleznete v tématu:

- [Příklady zarovnání](#vclrfalignexamples)

- [Definování nových typů s __declspec(align(#))](#vclrf_declspecaligntypedef)

- [Zarovnávání dat v lokální úložiště vláken](#vclrfthreadlocalstorageallocation)

- [Jak zarovnat funguje s okolních dat](#vclrfhowalignworkswithdatapacking)

- [Příklady zarovnání struktur](../build/examples-of-structure-alignment.md) (x64 konkrétní)

##  <a name="vclrfalignexamples"></a> Příklady zarovnání

Následující příklady zobrazují jak `__declspec(align(#))` má vliv na velikost a zarovnání struktur data. Příklady předpokládají následující definice:

```cpp
#define CACHE_LINE  32
#define CACHE_ALIGN __declspec(align(CACHE_LINE))
```

V tomto příkladu `S1` struktura je definována pomocí `__declspec(align(32))`. Všechna použití `S1` pro definici proměnné nebo jiný typ deklarace jsou zarovnána 32 bajtů. `sizeof(struct S1)` Vrátí 32, a `S1` má 16 bajtů odsazení následující 16 bajtů požadovaných k uložení čtyři celých čísel. Každý `int` člen vyžaduje 4bajtový zarovnání, ale je deklarován jako 32 zarovnání struktury sám sebe. Proto celkové zarovnání je 32.

```cpp
struct CACHE_ALIGN S1 { // cache align all instances of S1
   int a, b, c, d;
};
struct S1 s1;   // s1 is 32-byte cache aligned
```

V tomto příkladu `sizeof(struct S2)` vrátí 16, které je právě součtem velikostí člena, protože se jedná násobkem požadavek na největší zarovnání (násobkem 8).

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

V tomto příkladu, Všimněte si, že `a` má zarovnání přirozené typ, v tomto případě 4 bajtů. Ale `S1` musí být 32 bajtů zarovnána. Dvacet osm bajtů odsazení postupujte podle `a`tak, aby `s1` spustí na posunu 32. `S4` potom dědí požadavek na zarovnání `S1`, protože se jedná o požadavek na největší zarovnání ve struktuře. `sizeof(struct S4)` Vrátí hodnotu 64.

```cpp
struct S4 {
   int a;
   // 28 bytes padding
    struct S1 s1;      // S4 inherits cache alignment requirement of S1
};
```

Následující tři deklarace proměnných také použít `__declspec(align(#))`. V každém případě proměnná musí být zarovnána 32 bajtů. V případě pole je základní adresa pole není každý člen pole zarovnán 32 bajtů. `sizeof` Hodnotu pro každý člen pole nemá vliv, pokud používáte `__declspec(align(#))`.

```cpp
CACHE_ALIGN int i;
CACHE_ALIGN int array[128];
CACHE_ALIGN struct s2 s;
```

Chcete-li zarovnat každý člen pole, by měl použít kód, například:

```cpp
typedef CACHE_ALIGN struct { int a; } S5;
S5 array[10];
```

V tomto příkladu Všimněte si, že zarovnání struktury sám a zarovnání první prvek mají stejný účinek:

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

`S6` a `S7` mít identické zarovnání a přidělení a velikost charakteristiky.

V tomto příkladu zarovnání počáteční adresy a, b, c, a d 4, 1, 4 a je 1, v uvedeném pořadí.

```cpp
void fn() {
   int a;
   char b;
   long c;
   char d[10]
}
```

Zarovnání při přidělení paměti v haldě závisí na přidělení funkci, která je volána.  Například, pokud používáte `malloc`, výsledek bude záviset na velikosti operand. Pokud *arg* > = 8, paměť vrátil, je zarovnána na 8 bajtů. Pokud *arg* < 8, zarovnání paměti vrátil je první power 2 menší než *arg*. Například pokud používáte malloc(7), zarovnání je 4 bajtů.

##  <a name="vclrf_declspecaligntypedef"></a> Definování nových typů s __declspec(align(#))

Můžete definovat typ se vlastnosti zarovnání.

Například můžete definovat `struct` s zarovnání hodnota tímto způsobem:

```cpp
struct aType {int a; int b;};
typedef __declspec(align(32)) struct aType bType;
```

Nyní `aType` a `bType` stejnou velikost (8 bajtů) ale proměnné typu `bType` jsou zarovnána 32 bajtů.

##  <a name="vclrfthreadlocalstorageallocation"></a> Zarovnávání dat v lokální úložiště vláken

Statické úložiště thread local (TLS) vytvořené pomocí `__declspec(thread)` atribut a vložit do části TLS ve službě funguje bitové kopie pro zarovnání úplně stejně jako normální statických dat. Vytvořit data protokolu TLS, operační systém přidělí paměť velikost oddílu TLS a respektuje atribut zarovnání oddílu TLS.

Tento příklad ukazuje různé způsoby, jak umístění zarovnaný dat do úložiště thread local.

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

##  <a name="vclrfhowalignworkswithdatapacking"></a> Jak zarovnat funguje s okolních dat

**/Zp** – možnost kompilátoru a `pack` – Direktiva pragma mít za následek balení data pro členové struktury a sjednocení. Tento příklad ukazuje, jak **/Zp** a `__declspec(align(#))` spolupracují:

```c[[]]
struct S {
   char a;
   short b;
   double c;
   CACHE_ALIGN double d;
   char e;
   double f;
};
```

Následující tabulka uvádí posun každý člen v rámci různých **/Zp** (nebo #pragma `pack`) hodnoty, znázorňující způsob, jakým dva komunikovat.

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

Posun objektu je založen na posun předchozího objektu a aktuální balení nastavení, pokud objekt má `__declspec(align(#))` atribut, v takovém případě je zarovnání podle posun předchozího objektu a `__declspec(align(#))` hodnotu objektu.

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)  
[Přehled konvencí ARM ABI](../build/overview-of-arm-abi-conventions.md)  
[Přehled konvencí volání v prostředí x64](../build/overview-of-x64-calling-conventions.md)  
