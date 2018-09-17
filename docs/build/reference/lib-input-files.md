---
title: Vstupní soubory LIB | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 952c3345234192e3798fea483d527cd3afec4bff
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702465"
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