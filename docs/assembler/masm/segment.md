---
title: SEGMENT
ms.date: 08/30/2018
f1_keywords:
- SEGMENT
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
ms.openlocfilehash: f37be47b92a71e20821cd1e40f8cf1350dfedaff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62210372"
---
# <a name="segment"></a>SEGMENT

Definuje segment program s názvem *název* s atributy segmentu

## <a name="syntax"></a>Syntaxe

> *název* SEGMENTU [[určené jen pro čtení]] [[*zarovnat*]] [[*kombinovat*]] [[*použít*]] [[*charakteristiky*]] ALIAS (*řetězec*) [["*třídy*.]]<br/>
> *Příkazy*<br/>
> *název* KONČÍ

#### <a name="parameters"></a>Parametry

*align*<br/>
Rozsah adresy paměti, ze kterých lze vybrat počáteční adresu segmentu. Typ zarovnání může být jedna z následujících akcí:

|Typ zarovnání|Počáteční adresa|
|----------------|----------------------|
|**BYTE**|Další adresa k dispozici bajtů.|
|**WORD**|Další adresa k dispozici word (2 bajty za word).|
|**DWORD**|Další adresa k dispozici double word (4 bajtů na typ double word).|
|**PARA**|Další adresa k dispozici odstavci (16 bajtů za odstavci).|
|**PAGE**|Další adresa k dispozici stránky (256 bajtů na stránku).|
|**ALIGN**(*n*)|Další dostupné *n*th bajtů adresu. Další informace jsou uvedeny v části poznámky.|

Pokud není tento parametr zadán, **PARA** se používá ve výchozím nastavení.

*combine*<br/>
**VEŘEJNÉ**, **zásobníku**, **běžné**, **paměti**, **na**<em>adresu</em>, **PRIVÁTNÍ**

*Použití*<br/>
**USE16**, **USE32**, **BEZ STROMOVÉ STRUKTURY**

*Vlastnosti*<br/>
**Informace o**, **čtení**, **zápisu**, **EXECUTE**, **SHARED**, **NOPAGE**, **NOCACHE**, a **ZAHOZENÍ**

Tyto jsou podporovaná jenom pro COFF a odpovídají vlastnostem oddílu COFF podobným názvem (například **SHARED** odpovídá IMAGE_SCN_MEM_SHARED). ČTENÍ nastaví příznak IMAGE_SCN_MEM_READ. Zastaralé příznaku READONLY způsobila části zrušte příznak IMG_SCN_MEM_WRITE. Pokud existuje *charakteristiky* je nastaveno, nejsou použity výchozí charakteristiky a jsou jenom příznaky programátor zadané aktivní.

`ALIAS(` *řetězec* `)`<br/>
Tento řetězec se používá jako název oddílu, který v emitovaný objekt COFF.  Vytváří více oddílů se stejným názvem externí, se liší názvy MASM segmentu.

Není podporováno s **/omf**.

*class*<br/>
Určuje, jak by měla být segmenty kombinovat a uspořádané v souboru sestavený. Typické hodnoty se `'DATA'`, `'CODE'`, `'CONST'` a `'STACK'`

## <a name="remarks"></a>Poznámky

Pro `ALIGN(n)`, *n* může být jakékoli Mocnina 2 od 1 do 8 192; nepodporuje **/omf**.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>