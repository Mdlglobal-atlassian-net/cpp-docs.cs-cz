---
title: Vstupní soubory LIB
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: 648871464dbc99972b8ca40579046347727e81cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269385"
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

## <a name="see-also"></a>Viz také:

[Přehled knihovny LIB](overview-of-lib.md)
