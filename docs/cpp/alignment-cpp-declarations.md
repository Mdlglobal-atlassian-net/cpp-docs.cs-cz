---
title: Zarovnání (deklarace C++)
description: Způsob, jakým je zarovnání dat C++určeno v moderních.
ms.date: 09/19/2019
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: 67debc00343b8bee4184e020c9269011e2fcebc9
ms.sourcegitcommit: f907b15f50a6b945d0b87c03af0050946157d701
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2019
ms.locfileid: "71158749"
---
# <a name="alignment-c-declarations"></a>Zarovnání (deklarace C++)

Jednou z funkcí nižší úrovně C++ je možnost určit přesné zarovnání objektů v paměti, aby bylo možné využít maximální využití konkrétní hardwarové architektury. Ve výchozím nastavení `bool` kompilátor zarovnává členy třídy a struktury s hodnotou velikosti: a `char` na hranici 1 bajtu, `short` na hranicích na 2 bajtech, `int` `long`, a `float` na hranicích 4 bajtů a `long long`, ana`long double` hranici 8 bajtů. `double` Ve většině scénářů nikdy nemusíte mít obavy o zarovnání, protože výchozí zarovnání je již optimální. V některých případech ale můžete dosáhnout výrazného zvýšení výkonu nebo úspory paměti tím, že zadáte vlastní zarovnání vašich datových struktur. Před Visual Studio 2015 můžete použít klíčová slova `__alignof` specifická pro společnost Microsoft a `declspec(alignas)` zadat zarovnání větší než výchozí. Počínaje verzí Visual Studio 2015 byste měli použít standardní klíčová slova C++ 11 [alignof a alignas](../cpp/alignof-and-alignas-cpp.md) pro maximální přenositelnost kódu. Nová klíčová slova se chovají stejným způsobem jako v digestoři jako rozšíření specifická pro společnost Microsoft. Dokumentace pro tato rozšíření platí také pro nová klíčová slova. Další informace naleznete v tématu [operátor __alignof](../cpp/alignof-operator.md) a [align](../cpp/align-cpp.md). C++ Standard neurčuje chování při sbalení pro zarovnání na hranicích menších, než je výchozí kompilátor pro cílovou platformu, takže v takovém případě je stále nutné použít sadu Microsoft #pragma [Pack](../preprocessor/pack.md) .

Pro přidělení paměti datových struktur s vlastními zarovnání použijte [třídu aligned_storage](../standard-library/aligned-storage-class.md) . [Třída aligned_union](../standard-library/aligned-union-class.md) slouží k určení zarovnání pro sjednocení s netriviálními konstruktory nebo destruktory.

## <a name="about-alignment"></a>O zarovnání

Zarovnání je vlastnost adresy paměti vyjádřená jako číselná adresa modulo 2. Například adresa 0x0001103F modulo 4 je 3. Tato adresa se označuje jako zarovnaná na 4n + 3, kde 4 značí zvolenou mocninu 2. Zarovnání adresy závisí na zvolené mocnině 2. Stejná adresa modulo 8 je 7. Adresa je označována jako zarovnaná na X, pokud je jeho zarovnání Xn + 0.

CPU spouští instrukce, které pracují s daty uloženými v paměti. Data jsou identifikována svými adresami v paměti. Každé datum má také velikost. Zavoláme k němu *přirozeně zarovnané* , pokud je jeho adresa zarovnaná na jeho velikost. V opačném případě se nazývá *nesprávně* navýšení. Například datum desetinné čárky s plovoucí desetinnou čárkou je přirozeně zarovnané, pokud adresa použitá k identifikaci má 8bitové zarovnání.

## <a name="compiler-handling-of-data-alignment"></a>Zpracování zarovnání dat kompilátorem

Kompilátory se snaží vytvořit data způsobem, který zabraňuje chybnému zarovnání dat.

Pro jednoduché datové typy kompilátor přiřadí adresy, které jsou násobky velikosti v bajtech datového typu. Například kompilátor přiřadí adresy proměnným typu `long` , které jsou násobky 4, nastavení dolních 2 bitů adresy na nulu.

Kompilátor také Zapad struktury způsobem, který přirozeně zarovnává každý prvek struktury. Vezměte v úvahu `struct x_` strukturu v následujícím příkladu kódu:

```cpp
struct x_
{
   char a;     // 1 byte
   int b;      // 4 bytes
   short c;    // 2 bytes
   char d;     // 1 byte
} bar[3];
```

Kompilátor vyplní tuto strukturu, aby se vynutilo zarovnání přirozeně.

Následující příklad kódu ukazuje, jak kompilátor umístí čalouněnou strukturu do paměti:

```cpp
// Shows the actual memory layout
struct x_
{
   char a;            // 1 byte
   char _pad0[3];     // padding to put 'b' on 4-byte boundary
   int b;            // 4 bytes
   short c;          // 2 bytes
   char d;           // 1 byte
   char _pad1[1];    // padding to make sizeof(x_) multiple of 4
} bar[3];
```

Obě deklarace vrátí `sizeof(struct x_)` jako 12 bajtů.

Druhá deklarace obsahuje dva prvky odsazení:

1. `char _pad0[3]`pro zarovnávání `int b` členů na hranici 4 bajtů.

1. `char _pad1[1]`pro zarovnání prvků pole struktury `struct _x bar[3];` na hranici se čtyřmi bajty.

Odsazení zarovnává elementy `bar[3]` způsobem, který umožňuje přirozený přístup.

Následující příklad kódu ukazuje `bar[3]` rozložení pole:

```Output
adr offset   element
------   -------
0x0000   char a;         // bar[0]
0x0001   char pad0[3];
0x0004   int b;
0x0008   short c;
0x000a   char d;
0x000b   char _pad1[1];

0x000c   char a;         // bar[1]
0x000d   char _pad0[3];
0x0010   int b;
0x0014   short c;
0x0016   char d;
0x0017   char _pad1[1];

0x0018   char a;         // bar[2]
0x0019   char _pad0[3];
0x001c   int b;
0x0020   short c;
0x0022   char d;
0x0023   char _pad1[1];
```

## <a name="see-also"></a>Viz také:

[Zarovnání struktury dat](https://en.wikipedia.org/wiki/Data_structure_alignment)
