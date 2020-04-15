---
title: Konstanty variantních typů parametrů
ms.date: 11/04/2016
f1_keywords:
- VTS_YPOS_HIMETRIC
- VTS_PICTURE
- VTS_FONT
- VTS_XPOS_HIMETRIC
- VTS_XPOS_PIXELS
- VTS_XSIZE_HIMETRIC
- VTS_YPOS_PIXELS
- VTS_TRISTATE
- VTS_HANDLE
- VTS_YSIZE_HIMETRIC
- VTS_COLOR
- VTS_OPTEXCLUSIVE
- VTS_YSIZE_PIXELS
- VTS_XSIZE_PIXELS
helpviewer_keywords:
- VTS_XPOS_HIMETRIC constant [MFC]
- VTS_FONT constant [MFC]
- VTS_XPOS_PIXELS constant [MFC]
- VTS_COLOR constant [MFC]
- Variants [MFC]
- VTS_YPOS_PIXELS constant [MFC]
- VTS_YSIZE_HIMETRIC constant [MFC]
- VTS_YPOS_HIMETRIC constant [MFC]
- Variants, parameter type constants
- Variant data constants [MFC]
- VTS_PICTURE constant [MFC]
- VTS_TRISTATE constant [MFC]
- VTS_XSIZE_HIMETRIC constant [MFC]
- VTS_HANDLE constant [MFC]
- VTS_XSIZE_PIXELS constant [MFC]
- VTS_OPTEXCLUSIVE constant [MFC]
- VTS_YSIZE_PIXELS constant [MFC]
ms.assetid: de99c7a9-7aae-4dc4-b723-40c6380543ab
ms.openlocfilehash: f73c72830216679f8a91d0037d48c1e1b8e400c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372870"
---
# <a name="variant-parameter-type-constants"></a>Konstanty variantních typů parametrů

Toto téma obsahuje seznam nových konstant, které označují typy parametrů variant určených pro použití s třídami ovládacích prvků OLE knihovny tříd Microsoft Foundation.

Následuje seznam konstant třídy:

## <a name="variant-data-constants"></a><a name="_mfc_variant_data_constants"></a>Konstanty dat variant

- VTS_COLOR 32bitové celé číslo, které představovalo hodnotu barvy RGB.

- VTS_FONT Ukazatel na `IFontDisp` rozhraní objektu písma OLE.

- VTS_HANDLE Hodnota popisovače systému Windows.

- VTS_PICTURE Ukazatel na `IPictureDisp` rozhraní objektu obrázku OLE.

- VTS_OPTEXCLUSIVE 16bitová hodnota používaná pro ovládací prvek, který je určen k použití ve skupině ovládacích prvků, například přepínacích tlačítek. Tento typ říká kontejneru, že pokud jeden ovládací prvek ve skupině má hodnotu TRUE, všechny ostatní musí být FALSE.

- VTS_TRISTATE 16bitové podepsané celé číslo používané pro vlastnosti, které mohou mít jednu ze tří možných hodnot (vybraná, nepřístupná, nedostupná), například zaškrtávací políčko.

- VTS_XPOS_HIMETRIC 32bitové neznaménkové celé číslo, které představovalo pozici podél osy x v jednotkách HIMETRIC.

- VTS_YPOS_HIMETRIC 32bitové neznaménkové celé číslo, které představovalo pozici podél osy y v jednotkách HIMETRIC.

- VTS_XPOS_PIXELS 32bitové nepodepsané celé číslo, které představovalo pozici podél osy x v obrazových bodech.

- VTS_YPOS_PIXELS 32bitové nepodepsané celé číslo, které představovalo pozici podél osy y v obrazových bodech.

- VTS_XSIZE_PIXELS 32bitové nepodepsané celé číslo, které představovalo šířku objektu obrazovky v obrazových bodech.

- VTS_YSIZE_PIXELS 32bitové nepodepsané celé číslo, které představovalo výšku objektu obrazovky v obrazových bodech.

- VTS_XSIZE_HIMETRIC 32bitové nepodepsané celé číslo, které představovalo šířku objektu obrazovky v jednotkách HIMETRIC.

- VTS_YSIZE_HIMETRIC 32bitové nepodepsané celé číslo, které představovalo výšku objektu obrazovky v jednotkách HIMETRIC.

    > [!NOTE]
    >  Další konstanty variant byly definovány pro všechny typy variant, s výjimkou VTS_FONT a VTS_PICTURE, které poskytují ukazatel na konstantu dat varianty. Tyto konstanty jsou pojmenovány pomocí VTS_P`constantname` konvence. Například VTS_PCOLOR je ukazatel na VTS_COLOR konstantu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
