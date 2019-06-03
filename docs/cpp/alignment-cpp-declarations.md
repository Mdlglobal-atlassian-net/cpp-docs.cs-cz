---
title: Zarovnání (deklarace C++)
description: Způsob zarovnání dat je zadán v moderních C++.
ms.date: 05/30/2019
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: b6e03ac2b89624a0eb6602183d4ff4bf8b518f8d
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450767"
---
# <a name="alignment-c-declarations"></a>Zarovnání (deklarace C++)

Jednou z nízké úrovně funkcí jazyka C++ je schopnost určit přesné zarovnání objektů v paměti maximálně využijí architektury konkrétní hardware. Ve výchozím nastavení, kompilátor zarovná členy třídy a struktury na jejich velikost: `bool` a `char` na 1bajtových hranicích `short` na 2bajtových hranicích `int`, `long`, a `float` na 4bajtových hranicích a `long long`, `double`, a `long double` na hranice 8 bajtů. Ve většině scénářů si budete muset nikdy problémem zarovnání, protože je již optimální výchozí zarovnání. V některých případech však můžete dosáhnout výrazné zlepšení výkonu, nebo úspory paměti tak, že zadáte vlastní zarovnání datových struktur. Před Visual Studio 2015 můžete použít klíčová slova specifická pro společnost Microsoft `__alignof` a `declspec(alignas)` k určení zarovnání větší než výchozí. Spuštění v sadě Visual Studio 2015 používejte C ++ 11 standard klíčových slov [alignof a alignas](../cpp/alignof-and-alignas-cpp.md) pro přenositelnost maximální kódu. Nová klíčová slova se chovají stejným způsobem pod pokličkou jako rozšíření specifické pro společnost Microsoft. Dokumentace pro tato rozšíření platí také pro nová klíčová slova. Další informace najdete v tématu [__alignof – operátor](../cpp/alignof-operator.md) a [zarovnat](../cpp/align-cpp.md). C++ Standard neurčuje balení chování pro zarovnání na hranicích menší než výchozí nastavení kompilátoru pro cílovou platformu, tak budete stále muset použít Microsoft #pragma [pack](../preprocessor/pack.md) v takovém případě.

Použití [aligned_storage – třída](../standard-library/aligned-storage-class.md) pro přidělení paměti s vlastní zarovnání datových struktur. [Aligned_union – třída](../standard-library/aligned-union-class.md) slouží k určení zarovnání pro sjednocení s netriviálními konstruktory a destruktory.

## <a name="about-alignment"></a>Informace o zarovnání

Zarovnání je vlastností adresu paměti, vyjádřené jako číselné adresu modulo mocninou čísla 2. Například adresa 0x0001103F modulo 4 je 3. Tuto adresu se říká, že pro zarovnání na 4n + 3, kde označuje zvolený Mocnina 2, 4. Zarovnání adresu závisí na zvoleném Mocnina 2. Stejnou adresu modulo 8 je 7. Adresa se říká, že pro zarovnání na X, pokud je jeho zarovnání Xn + 0.

Procesory spouštění instrukcí, které pracují s daty uloženými v paměti. Data jsou identifikována podle jejich adresy v paměti. Velikost je také jeden datum. Označujeme je jako datum *přirozeně zarovnané* -li její adresa je umístěno na jeho velikost. Je volána *chybně zarovnaných* jinak. Pokud je adresa používaná k identifikaci ji 8bajtový zarovnání například přirozeně zarovnána 8 bajtů s plovoucí desetinnou čárkou datum.

## <a name="compiler-handling-of-data-alignment"></a>Kompilátor zpracování zarovnání dat

Kompilátory pokus o přidělení data způsobem, který brání chybné data.

Pro jednoduché datové typy kompilátor přiřadí adresy, které jsou násobky velikost v bajtech datového typu. Například kompilátor přiřadí adresy proměnné typu `long` , které jsou násobkem 4, nastavení 2 bitů adresy dole na nulu.

Kompilátor také vyplní struktury tak, aby přirozeně zarovná každý prvek struktury. Vezměte v úvahu strukturu `struct x_` v následujícím příkladu kódu:

```cpp
struct x_
{
   char a;     // 1 byte
   int b;      // 4 bytes
   short c;    // 2 bytes
   char d;     // 1 byte
} MyStruct;
```

Kompilátor vyplní tato struktura přirozeně vynutit zarovnání.

Následující příklad kódu ukazuje, jak kompilátor umístí vyplněný struktury v paměti:

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
}
```

1. Obě deklarace vrátit `sizeof(struct x_)` jako 12 bajtů.

1. Druhý deklarace obsahuje dva prvky odsazení:

1. `char _pad0[3]` aby bylo v souladu `int b` člena na hranici 4 bajty.

1. `char _pad1[1]` Zarovnat elementy pole struktury `struct _x bar[3];`

1. Odsazení se zarovná prvky `bar[3]` způsobem, který umožňuje přístup k fyzické.

Následující příklad kódu ukazuje `bar[3]` pole rozložení:

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
