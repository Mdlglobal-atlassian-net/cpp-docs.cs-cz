---
title: Úložiště bitových polí
ms.date: 11/04/2016
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
ms.openlocfilehash: 4dbfb3c6ad27fb023881dafde74bb27132959085
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147526"
---
# <a name="storage-of-bit-fields"></a>Úložiště bitových polí

**ANSI 3.5.2.1** pořadí přidělování bitových polí v rámci celé číslo

Bitová pole jsou přiděleny v rámci celé číslo z nejméně významné nejvýznamnější bit. V následujícím kódu

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

bity by být uspořádány takto:

```
00000001 11110010
cccccccb bbbbaaaa
```

Jelikož procesory 80x86 ukládají nižší bajt celočíselných hodnot před vyšší bajt, bude celé číslo 0x01F2 ve fyzické paměti uloženo jako 0xF2 následované 0x01.

## <a name="see-also"></a>Viz také:

[Struktury, sjednocení, výčty a bitová pole](../c-language/structures-unions-enumerations-and-bit-fields.md)
