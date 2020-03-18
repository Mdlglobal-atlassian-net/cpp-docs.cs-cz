---
title: Vstupní soubory LIB
ms.date: 11/04/2016
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: 209ba04ea43116b39f28b0790b7a1e2b3fb5ccd7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439441"
---
# <a name="lib-input-files"></a>Vstupní soubory LIB

Vstupní soubory, které očekává LIB, závisí na režimu, ve kterém se používá, jak je znázorněno v následující tabulce.

|Režim|Vstup|
|----------|-----------|
|Výchozí (sestavení nebo úprava knihovny)|Soubory objektů COFF (. obj), knihovny COFF (. lib), 32 soubory objektů (. obj) formátu OMF (model objektů objektu)|
|Extrahování člena pomocí/EXTRACT|Knihovna COFF (. lib)|
|Sestavení souboru exportu a import knihovny pomocí/DEF|Soubor definice modulu (. def), soubory objektů COFF (. obj), knihovny COFF (. lib), 32 soubory objektů OMF (. obj)|

> [!NOTE]
>  Knihovny OMF vytvořené 16bitovou verzí knihovny LIB nelze použít jako vstup do 32 verze knihovny LIB.

## <a name="see-also"></a>Viz také

[Přehled knihovny LIB](overview-of-lib.md)
