---
title: Vstupní soubory LIB
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: 885d03e74c7acff54e527c2dbad38de055913b5f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503310"
---
# <a name="lib-input-files"></a>Vstupní soubory LIB

Vstupní soubory LIB očekává závisí na režimu, ve kterém se používá se, jak je znázorněno v následující tabulce.

|Režim|Vstup|
|----------|-----------|
|Výchozí (vytvářejí nebo upravují knihovnu)|Soubory COFF objekt (.obj), COFF knihovny (.lib), soubory objektů (.obj) formátu omf modelu objektu (–) 32-bit|
|Extrahování člena s/extract|COFF knihovny (.lib)|
|Vytváření export soubor a importujte knihovnu s def|Soubor definice modulu (.def), soubory COFF objekt (.obj), COFF knihovny (.lib), 32-bit omf – soubory objektů (.obj)|

> [!NOTE]
>  Knihovny OMF vytvořené v 16bitové verzi produktu LIB nelze použít jako vstup pro 32bitovou verzi nástroje LIB.

## <a name="see-also"></a>Viz také

[Přehled knihovny LIB](../../build/reference/overview-of-lib.md)