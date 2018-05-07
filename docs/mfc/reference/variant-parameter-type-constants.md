---
title: Konstanty variantních typů parametrů | Microsoft Docs
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
ms.openlocfilehash: 13820ff4fb07c3743f36ba3ebe33ee56a3a79c7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="variant-parameter-type-constants"></a>Konstanty variantních typů parametrů
Toto téma uvádí nové konstanty, které indikují typy variant parametr určený k použití u třídy ovládacích prvků OLE z knihovny Microsoft Foundation Class.  
  
 Následuje seznam třída konstant:  
  
##  <a name="_mfc_variant_data_constants"></a> Variant – konstanty dat  
  
-   **Vts_color –** A 32bitové celé číslo představující hodnotu barva RGB.  
  
-   **Vts_font –** ukazatel **IFontDisp** rozhraní OLE písma objektu.  
  
-   **Vts_handle –** A Windows zpracování hodnotu.  
  
-   **Vts_picture –** ukazatel `IPictureDisp` rozhraní OLE objektu obrázku.  
  
-   **Vts_optexclusive –** A 16bitové hodnoty používané pro ovládací prvek, který je určen pro použití ve skupině ovládacích prvků, jako jsou přepínače. Tento typ informuje kontejneru, pokud jedna kontrolovat v skupinu má **TRUE** hodnota, všechny ostatní musí být **FALSE**.  
  
-   **Vts_tristate –** A 16bitové celé číslo se znaménkem používá pro vlastnosti, které může mít jeden ze tří možných hodnot (vybrané, nezaškrtnuté, není k dispozici), například zaškrtávací políčko.  
  
-   **Vts_xpos_himetric –** A 32bitové celé číslo bez znaménka používá k reprezentování pozice podél osy x v **HIMETRIC** jednotky.  
  
-   **Vts_ypos_himetric –** A 32bitové celé číslo bez znaménka používá k reprezentování pozice podél osy y v **HIMETRIC** jednotky.  
  
-   **Vts_xpos_pixels –** A 32bitové celé číslo bez znaménka používá k reprezentování pozice podél osy x v pixelech.  
  
-   **Vts_ypos_pixels –** A 32bitové celé číslo bez znaménka používá k reprezentování pozice podél osy y v pixelech.  
  
-   **Vts_xsize_pixels –** A 32bitové celé číslo bez znaménka používá k reprezentování šířku objektu na obrazovce v pixelech.  
  
-   **Vts_ysize_pixels –** A 32bitové celé číslo bez znaménka používá k reprezentování výška objektu na obrazovce v pixelech.  
  
-   **Vts_xsize_himetric –** A 32bitové celé číslo bez znaménka používá k reprezentování šířku objektu obrazovky v **HIMETRIC** jednotky.  
  
-   **Vts_ysize_himetric –** A 32bitové celé číslo bez znaménka používá k reprezentování výška objektu obrazovky v **HIMETRIC** jednotky.  
  
    > [!NOTE]
    >  Další variant konstanty nebyly definovány pro všechny typy variant, s výjimkou produktů **vts_font –** a **vts_picture –**, které poskytují ukazatel na zařízení ve vlastnictví firmy dat variant nstant. Tyto konstanty jsou pojmenované pomocí **VTS_P** `constantname` konvence. Například **VTS_PCOLOR** je ukazatel na **vts_color –** konstantní.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
