---
title: Funkce gray a dithered pro bitové mapy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
dev_langs:
- C++
helpviewer_keywords:
- gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd0a0a25e1607b3b4318fdfca1f68f272cd02173
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380188"
---
# <a name="gray-and-dithered-bitmap-functions"></a>Funkce Gray a Dithered pro bitové mapy

**Funkce Gray mapy**

Knihovna MFC poskytuje dvě funkce pro poskytování rastrový obrázek vzhledu ovládacího prvku zakázané.

![Porovnání ikonu šedé a původní verzí](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")

|||
|-|-|
|[Afxdrawgraybitmap –](#afxdrawgraybitmap)|Nakreslí šedé verzi rastrový obrázek.|
|[Afxgetgraybitmap –](#afxgetgraybitmap)|Zkopíruje šedé verzi rastrový obrázek.|

**Funkce dithered pro bitové mapy**

Knihovna MFC poskytuje dvě funkce také pro nahrazení vzoru dithered pro bitové rastrový obrázek na pozadí.

![Porovnání ikonu dithered pro bitové a původní verzí](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

|||
|-|-|
|[Afxdrawditheredbitmap –](#afxdrawditheredbitmap)|Nakreslí rastrový obrázek s dithered pro bitové na pozadí.|
|[Afxgetditheredbitmap –](#afxgetditheredbitmap)|Zkopíruje bitmapu s dithered pro bitové na pozadí.|

##  <a name="afxdrawgraybitmap"></a>  Afxdrawgraybitmap –

Nakreslí šedé verzi rastrový obrázek.

```
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF crBackground);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
Odkazuje na cílový řadič domény.

*x*<br/>
Cílové souřadnice x.

*y*<br/>
Cílové souřadnice na ose y.

*rSrc*<br/>
Zdrojovou bitmapu.

*crBackground*<br/>
Nová barva pozadí (obvykle zašedlé, jako je například COLOR_MENU).

### <a name="remarks"></a>Poznámky

Rastrový obrázek nakreslit `AfxDrawGrayBitmap` bude mít vzhled zablokovaný ovládací prvek.

![Porovnání ikonu šedé a původní verzí](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="afxgetgraybitmap"></a>  Afxgetgraybitmap –

Zkopíruje šedé verzi rastrový obrázek.

```
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF crBackground);
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Zdrojovou bitmapu.

*pDest*<br/>
Cílovou bitmapu.

*crBackground*<br/>
Nová barva pozadí (obvykle zašedlé, jako je například COLOR_MENU).

### <a name="remarks"></a>Poznámky

Rastrový obrázek zkopírováno spolu s `AfxGetGrayBitmap` bude mít vzhled zablokovaný ovládací prvek.

![Porovnání ikonu šedé a původní verzí](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="afxdrawditheredbitmap"></a>  Afxdrawditheredbitmap –

Nakreslí rastrový obrázek, jeho pozadí nahrazení vzoru dithered pro bitové (kontroly).

```
void AFXAPI AfxDrawDitheredBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
Odkazuje na cílový řadič domény.

*x*<br/>
Cílové souřadnice x.

*y*<br/>
Cílové souřadnice na ose y.

*rSrc*<br/>
Zdrojovou bitmapu.

*cr1*<br/>
Jednu z dvou tónování barev, obvykle bílou.

*CR2*<br/>
Další tónování barvu, obvykle světle šedá (COLOR_MENU).

### <a name="remarks"></a>Poznámky

Zdrojovou bitmapu je vykreslen na cílový řadič domény s dvěma barvami (*cr1* a *cr2*) šachovnicová mřížka vzor nahrazení rastrového obrázku na pozadí. Pozadí zdrojovou bitmapu je definován jako jeho bílé pixelů a všechny obrazové body odpovídající barva pixel v levém horním rohu rastrového obrázku.

![Porovnání ikonu dithered pro bitové a původní verzí](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h


##  <a name="afxgetditheredbitmap"></a>  Afxgetditheredbitmap –

Zkopíruje bitmapu, jeho pozadí nahrazení vzoru dithered pro bitové (kontroly).

```
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Zdrojovou bitmapu.

*pDest*<br/>
Cílovou bitmapu.

*cr1*<br/>
Jednu z dvou tónování barev, obvykle bílou.

*CR2*<br/>
Další tónování barvu, obvykle světle šedá (COLOR_MENU).

### <a name="remarks"></a>Poznámky

Zdrojová bitmapa nezkopíruje do cílové bitmapy barvou dvou (*cr1* a *cr2*) šachovnicová mřížka vzor nahrazení zdrojovou bitmapu na pozadí. Pozadí zdrojovou bitmapu je definován jako jeho bílé pixelů a všechny obrazové body odpovídající barva pixel v levém horním rohu rastrového obrázku.

![Porovnání ikonu dithered pro bitové a původní verzí](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
