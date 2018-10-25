---
title: Coloradjustment – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COLORADJUSTMENT
dev_langs:
- C++
helpviewer_keywords:
- COLORADJUSTMENT structure [MFC]
ms.assetid: 67fc4e63-0e0e-4fcb-8c45-aa5ebfefa013
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 682bbe2e9a4987ca30614e9210198193de977e3e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066289"
---
# <a name="coloradjustment-structure"></a>COLORADJUSTMENT – struktura

`COLORADJUSTMENT` Struktury definuje barvu úpravy hodnot použitých Windows `StretchBlt` a `StretchDIBits` funkce při `StretchBlt` POLOTÓNOVÁNÍ je režim.

## <a name="syntax"></a>Syntaxe

```
typedef struct  tagCOLORADJUSTMENT {    /* ca */
    WORD caSize;
    WORD caFlags;
    WORD caIlluminantIndex;
    WORD caRedGamma;
    WORD caGreenGamma;
    WORD caBlueGamma;
    WORD caReferenceBlack;
    WORD caReferenceWhite;
    SHORT caContrast;
    SHORT caBrightness;
    SHORT caColorfulness;
    SHORT caRedGreenTint;
} COLORADJUSTMENT;
```

#### <a name="parameters"></a>Parametry

*caSize*<br/>
Určuje velikost struktury v bajtech.

*caFlags*<br/>
Určuje, jak by měly být připraveny výstupní image. Tento člen lze nastavit na hodnotu NULL nebo libovolnou kombinaci následujícího:

- CA_NEGATIVE Určuje, zda má být zobrazena záporné hodnoty původní bitové kopie.

- CA_LOG_FILTER určuje logaritmické funkce, se použijí pro hustotu finální výstup barev. Při nízkém jas tím zvýší na barevný kontrast.

*caIlluminantIndex*<br/>
Určuje světelnost ke zdroji světla pod kterým je objekt obrázek zobrazit. Tento člen můžete nastavit na jedno z následujících hodnot:

- ILLUMINANT_EQUAL_ENERGY

- ILLUMINANT_A

- ILLUMINANT_B

- ILLUMINANT_C

- ILLUMINANT_D50

- ILLUMINANT_D55

- ILLUMINANT_D65

- ILLUMINANT_D75

- ILLUMINANT_F2

- ILLUMINANT_TURNGSTEN

- ILLUMINANT_DAYLIGHT

- ILLUMINANT_FLUORESCENT

- ILLUMINANT_NTSC

*caRedGamma*<br/>
Určuje hodnotu korekce gama n-tý power red primární zdroj barvy. Hodnota musí být v rozsahu od 2 500 do 65,000. Korekce gama znamená, že hodnota 10 000.

*caGreenGamma*<br/>
Určuje hodnotu korekce gama n-tý power zelené primární zdroj barvy. Hodnota musí být v rozsahu od 2 500 do 65,000. Korekce gama znamená, že hodnota 10 000.

*caBlueGamma*<br/>
Určuje hodnotu korekce gama n-tý power modré primární zdroj barvy. Hodnota musí být v rozsahu od 2 500 do 65,000. Korekce gama znamená, že hodnota 10 000.

*caReferenceBlack*<br/>
Určuje černé odkaz pro zdrojové barvy. Libovolné barvy, které jsou o něco tmavší než to jsou považovány za black. Hodnota musí být v rozsahu od 0 do 4000.

*caReferenceWhite*<br/>
Určuje bílé odkaz pro zdrojové barvy. Libovolné barvy, které jsou míň než toto jsou považovány za prázdné. Hodnota musí být v rozsahu od 6 000 do 10 000.

*caContrast*<br/>
Určuje množství kontrast, použijí se zdrojovým objektem. Hodnota musí být v rozsahu od -100 až 100. Hodnota 0 znamená, že žádné kontrast.

*caBrightness*<br/>
Určuje množství jas uplatňovat se zdrojovým objektem. Hodnota musí být v rozsahu od -100 až 100. Hodnota 0 znamená, že žádná úprava jas.

*caColorfulness*<br/>
Určuje množství colorfulness uplatňovat se zdrojovým objektem. Hodnota musí být v rozsahu od -100 až 100. Hodnota 0 znamená, že žádná úprava colorfulness.

*caRedGreenTint*<br/>
Určuje množství úpravy červenou nebo zelenou TINT – použije se zdrojovým objektem. Hodnota musí být v rozsahu od -100 až 100. Kladná čísla by upravte směrem k red a záporná čísla upravit na zelenou. 0 znamená, že žádná úprava odstín.

## <a name="requirements"></a>Požadavky

**Záhlaví:** wingdi.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetColorAdjustment](../../mfc/reference/cdc-class.md#getcoloradjustment)

