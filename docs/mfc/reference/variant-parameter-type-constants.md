---
title: Konstanty variantních typů parametrů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d61930bda4560baaf628ce018cc0161527d9d07e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885946"
---
# <a name="variant-parameter-type-constants"></a>Konstanty variantních typů parametrů
Toto téma obsahuje seznam nových konstanty, které označují typy parametr typu variant určený pro použití s OLE – třídy ovládacích prvků z knihovny Microsoft Foundation Class.  
  
 Následuje seznam konstant třídy:  
  
##  <a name="_mfc_variant_data_constants"></a> Variant – konstanty dat  
  
-   VTS_COLOR A 32bitové celé číslo představující hodnotu barvy RGB.  
  
-   VTS_FONT A ukazatel `IFontDisp` rozhraní písmo objektu OLE.  
  
-   Hodnota popisovače VTS_HANDLE A Windows.  
  
-   VTS_PICTURE A ukazatel `IPictureDisp` rozhraní obrázek objektu OLE.  
  
-   VTS_OPTEXCLUSIVE byla použita pro ovládací prvek, který je určen pro použití ve skupině ovládacích prvků, jako je například přepínačů hodnota A 16 bitů. Tento typ sdělí kontejneru, pokud jeden ovládací prvek ve skupině má hodnotu TRUE, všechny ostatní musí mít hodnotu FALSE.  
  
-   VTS_TRISTATE A 16bitové celé číslo se znaménkem používají pro vlastnosti, které může mít jednu ze tří možných hodnot (vybrané, nezaškrtnuté, není k dispozici), například zaškrtávací políčko.  
  
-   VTS_XPOS_HIMETRIC A 32bitové celé číslo bez znaménka představující pozici společně osu x v jednotkách HIMETRIC.  
  
-   VTS_YPOS_HIMETRIC A 32bitové celé číslo bez znaménka představující umístění podél osy y v jednotkách HIMETRIC.  
  
-   VTS_XPOS_PIXELS A 32bitové celé číslo bez znaménka představující pozici společně osu x v pixelech.  
  
-   VTS_YPOS_PIXELS A 32bitové celé číslo bez znaménka představující umístění podél osy y v pixelech.  
  
-   VTS_XSIZE_PIXELS A 32bitové celé číslo bez znaménka představující šířku objektu na obrazovce v pixelech.  
  
-   VTS_YSIZE_PIXELS A 32bitové celé číslo bez znaménka představující výšku objektu na obrazovce v pixelech.  
  
-   VTS_XSIZE_HIMETRIC A 32bitové celé číslo bez znaménka představující šířku objektu na obrazovce v jednotkách HIMETRIC.  
  
-   VTS_YSIZE_HIMETRIC A 32bitové celé číslo bez znaménka představující výšku objektu na obrazovce v jednotkách HIMETRIC.  
  
    > [!NOTE]
    >  Další varianty konstanty byly definovány pro všechny varianty typy, s výjimkou VTS_FONT a VTS_PICTURE, poskytující ukazatel na konstantu dat variant. Tyto konstanty jsou pojmenované pomocí VTS_P`constantname` konvence. Například VTS_PCOLOR je ukazatel na VTS_COLOR – konstanta.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
