---
title: Příklady zarovnání struktur
ms.date: 11/19/2018
helpviewer_keywords:
- structure alignment
- examples [C++], structure alignment
ms.assetid: 03d137bf-5cc4-472e-9583-6498f2534199
ms.openlocfilehash: 7c4b3ae29674e9c4fc27e8e175867339001b9a0d
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175337"
---
# <a name="examples-of-structure-alignment"></a>Příklady zarovnání struktur

Následující čtyři příklady každou deklaraci že zarovnané struktury nebo sjednocení a odpovídající obrázky znázorňují rozložení této struktury nebo sjednocení v paměti. Každý sloupec v elementu figure reprezentuje bajt paměti a číslo ve sloupci určuje posunutí daného bajtu. Název ve druhém řádku každý obrázek odpovídá názvu proměnné v prohlášení. Sloupců indikoval odsazení, která je potřebná k dosažení zadané zarovnání.

## <a name="example-1"></a>Příklad 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![Rozložení struktury – Příklad 1 převod AMD](../build/media/vcamd_conv_ex_1_block.png "AMD převod – Příklad 1 struktuře rozložení")

## <a name="example-2"></a>Příklad 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![Rozložení struktury příklad 2 převod AMD](../build/media/vcamd_conv_ex_2_block.png "AMD převod příklad 2 struktuře rozložení")

## <a name="example-3"></a>Příklad 3

```C
// Total size = 22 bytes, alignment = 4 bytes (doubleword).

_declspec(align(4)) struct {
    char a;       // +0; size = 1 byte
    short b;      // +2; size = 2 bytes
    char c;       // +4; size = 1 byte
    int d;        // +8; size = 4 bytes
}
```

![Rozložení struktury příklad 2 převod AMD](../build/media/vcamd_conv_ex_3_block.png "AMD převod příklad 2 struktuře rozložení")

## <a name="example-4"></a>Příklad 4:

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![Sjednocení layouit příklad 4: AMD převod](../build/media/vcamd_conv_ex_4_block.png "sjednocení layouit AMD převod příklad 4:")

## <a name="see-also"></a>Viz také:

[Typy a úložiště](../build/types-and-storage.md)<br/>
