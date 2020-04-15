---
title: Vstupní soubory LIB
ms.date: 11/04/2016
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: de81f79eecf3fc73c02894747f4b97cb107cf892
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328233"
---
# <a name="lib-input-files"></a>Vstupní soubory LIB

Vstupní soubory očekávané lib závisí na režimu, ve kterém se používá, jak je znázorněno v následující tabulce.

|Mode|Vstup|
|----------|-----------|
|Výchozí (vytvoření nebo úprava knihovny)|Soubory objektu COFF (.obj), knihovny COFF (.lib), 32bitové objektové soubory Objektový model (OMF) (.obj)|
|Extrahování člena pomocí /EXTRACT|Knihovna COFF (.lib)|
|Vytváření exportního souboru a importu knihovny s parametrem /DEF|Soubor definice modulu (.def), soubory objektu COFF (.obj), knihovny COFF (.lib), 32bitové soubory objektu OMF (.obj)|

> [!NOTE]
> Knihovny OMF vytvořené 16bitovou verzí LIB nelze použít jako vstup do 32bitové verze LIB.

## <a name="see-also"></a>Viz také

[Přehled knihovny LIB](overview-of-lib.md)
