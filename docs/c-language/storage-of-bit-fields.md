---
title: Úložiště bitových polí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c39fa4455cfdc387ab5aa2068c80494a4a8810ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020081"
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

## <a name="see-also"></a>Viz také

[Struktury, sjednocení, výčty a bitová pole](../c-language/structures-unions-enumerations-and-bit-fields.md)