---
title: Chyba linkerů LNK2004
ms.date: 11/04/2016
f1_keywords:
- LNK2004
helpviewer_keywords:
- LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
ms.openlocfilehash: 0d26ab12c5b82d52b7dcbb176d9bfa033d7ddfee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194834"
---
# <a name="linker-tools-error-lnk2004"></a>Chyba linkerů LNK2004

přetečení relativní opravy GP na target; krátký oddíl ' Section ' je příliš velký nebo mimo rozsah.

Oddíl je moc velký.

Chcete-li tuto chybu vyřešit, zmenšete velikost krátkého oddílu, buď explicitním vložením dat do dlouhých oddílů, pomocí #pragma oddílu (". sectionGroup", čtení, zápisu, Long) a použití `__declspec(allocate(".sectionname"))` v definicích a deklaracích dat.  Například:

```
#pragma section(".data$mylong", read, write, long)
__declspec(allocate(".data$mylong"))
char    rg0[1] = { 1 };
char    rg1[2] = { 1 };
char    rg2[4] = { 1 };
char    rg3[8] = { 1 };
char    rg4[16] = { 1 };
char    rg5[32] = { 1 };
```

Můžete také přesunout logicky seskupená data do vlastní struktury, která bude kolekcí dat větší než 8 bajtů, které kompilátor bude přidělovat v sekci s dlouhými daty.  Například:

```
// from this...
int     w1  = 23;
int     w2 = 46;
int     w3 = 23*3;
int     w4 = 23*4;

// to this...
struct X {
    int     w1;
    int     w2;
    int     w3;
    int     w4;
} x  = { 23, 23*2, 23*3, 23*4 };
```

Tato chyba je následována závažnou chybou `LNK1165`.
