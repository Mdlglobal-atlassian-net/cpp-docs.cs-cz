---
title: Coloradjustment – struktura | Microsoft Docs
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
ms.openlocfilehash: ffb0ec0233edd968ad121b84f9e1d584a26f3387
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369961"
---
# <a name="coloradjustment-structure"></a>COLORADJUSTMENT – struktura
`COLORADJUSTMENT` Struktura definuje barvu úpravu hodnoty používané Windows `StretchBlt` a **StretchDIBits** funkce při `StretchBlt` režim je **POLOTÓNOVÁNÍ**.  
  
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
 *caSize*  
 Určuje velikost struktury v bajtech.  
  
 *caFlags*  
 Určuje, jak je třeba připravit bitovou kopii výstupu. Tento člen může být nastaven na **NULL** nebo libovolnou kombinaci těchto hodnot:  
  
- **CA_NEGATIVE** Určuje, že se mají zobrazit záporné původní bitové kopie.  
  
- **CA_LOG_FILTER** Určuje, že hodnota na logaritmické funkce má být použita na konečné hustotu barvy výstup. Tím se zvýší barevný kontrast při nízkém světlostí.  
  
 *caIlluminantIndex*  
 Určuje světlostí zdroje světla, pod kterým je zobrazit objekt bitové kopie. Tento člen můžete nastavit na jedno z následujících hodnot:  
  
- **ILLUMINANT_EQUAL_ENERGY**  
  
- **ILLUMINANT_A**  
  
- **ILLUMINANT_B**  
  
- **ILLUMINANT_C**  
  
- **ILLUMINANT_D50**  
  
- **ILLUMINANT_D55**  
  
- **ILLUMINANT_D65**  
  
- **ILLUMINANT_D75**  
  
- **ILLUMINANT_F2**  
  
- **ILLUMINANT_TURNGSTEN**  
  
- **ILLUMINANT_DAYLIGHT**  
  
- **ILLUMINANT_FLUORESCENT**  
  
- **ILLUMINANT_NTSC**  
  
 *caRedGamma*  
 Určuje hodnotu n-tou power korekce gama red primární zdroj barev. Hodnota musí být v rozsahu od 2 500 do 65,000. Hodnota 10 000 znamená žádné korekce gama.  
  
 *caGreenGamma*  
 Určuje hodnotu n-tou power korekce gama zelená primární zdroj barev. Hodnota musí být v rozsahu od 2 500 do 65,000. Hodnota 10 000 znamená žádné korekce gama.  
  
 *caBlueGamma*  
 Určuje hodnotu korekce gama n-tou napájení blue primární zdroj barev. Hodnota musí být v rozsahu od 2 500 do 65,000. Hodnota 10 000 znamená žádné korekce gama.  
  
 *caReferenceBlack*  
 Určuje černým odkaz pro zdrojové barvy. Všechny barev, které jsou tmavší než to jsou považovány za černé. Hodnota musí být v rozsahu od 0 do 4 000.  
  
 *caReferenceWhite*  
 Určuje bílé odkaz pro zdrojové barvy. Všechny barev, které jsou písmo, než to jsou považovány za prázdné. Hodnota musí být v rozsahu od 6000 do 10 000.  
  
 *caContrast*  
 Určuje množství kontrast má být použita ke zdrojovému objektu. Hodnota musí být v rozsahu od -100 do 100. Hodnota 0 znamená bez úpravy kontrastu.  
  
 *caBrightness*  
 Určuje množství také průraznost má být použita ke zdrojovému objektu. Hodnota musí být v rozsahu od -100 do 100. Hodnota 0 znamená bez také průraznost úpravy.  
  
 *caColorfulness*  
 Určuje množství colorfulness má být použita ke zdrojovému objektu. Hodnota musí být v rozsahu od -100 do 100. Hodnota 0 znamená bez colorfulness úpravy.  
  
 *caRedGreenTint*  
 Určuje množství červené nebo zelené TINT – úpravy má být použita ke zdrojovému objektu. Hodnota musí být v rozsahu od -100 do 100. Kladná čísla by upravte směrem red a záporná čísla upravit směrem zeleně. 0 znamená bez TINT – úpravy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** wingdi.h systému  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetColorAdjustment](../../mfc/reference/cdc-class.md#getcoloradjustment)


