---
title: Úložiště bitových polí
ms.date: 11/04/2016
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
ms.openlocfilehash: 4dbfb3c6ad27fb023881dafde74bb27132959085
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157880"
---
# <a name="storage-of-bit-fields"></a>Úložiště bitových polí

**3.5.2.1 ANSI** Pořadí přidělení bitových polí v rámci typu int

Bitová pole jsou přidělována v rámci celého čísla z nejméně významných bitů. V následujícím kódu

```
struct mybitfields
{
   unsigned a : 4;
   unsigned b : 5;
   unsigned c : 7;
} test;

int main( void )
{
   test.a = 2;
   test.b = 31;
   test.c = 0;
}
```

bity budou uspořádány takto:

```
00000001 11110010
cccccccb bbbbaaaa
```

Jelikož procesory 80x86 ukládají nižší bajt celočíselných hodnot před vyšší bajt, bude celé číslo 0x01F2 ve fyzické paměti uloženo jako 0xF2 následované 0x01.

## <a name="see-also"></a>Viz také

[Struktury, sjednocení, výčty a bitová pole](../c-language/structures-unions-enumerations-and-bit-fields.md)
