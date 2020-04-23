---
title: Funkce Gray a Dithered pro bitové mapy
ms.date: 11/19/2018
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
helpviewer_keywords:
- gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
ms.openlocfilehash: a220596b880ee74d5f9ebf683d087156224ee7c5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751477"
---
# <a name="gray-and-dithered-bitmap-functions"></a>Funkce Gray a Dithered pro bitové mapy

**Šedé bitmapové funkce**

Knihovna MFC poskytuje dvě funkce pro poskytnutí vzhledu zakázaného ovládacího prvku rastrovým plánem.

![Porovnání verzí šedých a originálních ikon](../../mfc/reference/media/vcgraybitmap.gif "Porovnání verzí šedých a originálních ikon")

|||
|-|-|
|[AfxDrawGrayBitmap](#afxdrawgraybitmap)|Nakreslí šedou verzi rastrového plánu.|
|[AfxGetGrayBitmap](#afxgetgraybitmap)|Zkopíruje šedou verzi rastrového plánu.|

**Funkce rozpaků bitmap**

Knihovna MFC také poskytuje dvě funkce pro nahrazení pozadí bitmapy rozkladem vzorku.

![Porovnání roztírených a původních verzí ikon](../../mfc/reference/media/vcditheredbitmap.gif "Porovnání roztírených a původních verzí ikon")

|||
|-|-|
|[AfxDrawDitheredBitmap](#afxdrawditheredbitmap)|Nakreslí bitmapu s roztíraným pozadím.|
|[AfxGetDitheredBitmap](#afxgetditheredbitmap)|Zkopíruje bitmapu s roztíraným pozadím.|

## <a name="afxdrawgraybitmap"></a><a name="afxdrawgraybitmap"></a>AfxDrawGrayBitmap

Nakreslí šedou verzi rastrového plánu.

```cpp
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF crBackground);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazuje na cílový řadič domény.

*X*<br/>
Cíl oválná souřadnice x.

*Y*<br/>
Cílová souřadnice y.

*rSrc*<br/>
Zdrojová bitmapa.

*crPozadí*<br/>
Nová barva pozadí (obvykle šedá, například COLOR_MENU).

### <a name="remarks"></a>Poznámky

Bitmapa nakreslená `AfxDrawGrayBitmap` bude mít vzhled zakázaného ovládacího prvku.

![Porovnání verzí šedých a originálních ikon](../../mfc/reference/media/vcgraybitmap.gif "Porovnání verzí šedých a originálních ikon")

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="afxgetgraybitmap"></a><a name="afxgetgraybitmap"></a>AfxGetGrayBitmap

Zkopíruje šedou verzi rastrového plánu.

```cpp
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF crBackground);
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Zdrojová bitmapa.

*pDest*<br/>
Cílová bitmapa.

*crPozadí*<br/>
Nová barva pozadí (obvykle šedá, například COLOR_MENU).

### <a name="remarks"></a>Poznámky

Bitmapa zkopírovaná pomocí `AfxGetGrayBitmap` bude mít vzhled zakázaného ovládacího prvku.

![Porovnání verzí šedých a originálních ikon](../../mfc/reference/media/vcgraybitmap.gif "Porovnání verzí šedých a originálních ikon")

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="afxdrawditheredbitmap"></a><a name="afxdrawditheredbitmap"></a>AfxDrawDitheredBitmap

Nakreslí rastrový obrázek a nahradí jeho pozadí rozkladem (šachovním) vzorem.

```cpp
void AFXAPI AfxDrawDitheredBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazuje na cílový řadič domény.

*X*<br/>
Cíl oválná souřadnice x.

*Y*<br/>
Cílová souřadnice y.

*rSrc*<br/>
Zdrojová bitmapa.

*cr1*<br/>
Jedna ze dvou barev rozpisu barev, typicky bílá.

*cr2*<br/>
Další barva rozpisu barev, obvykle světle šedá (COLOR_MENU).

### <a name="remarks"></a>Poznámky

Zdrojová bitmapa je nakreslena na cílovém řadiči domény s dvoubarevným *(cr1* a *cr2)* šachovným vzorkem nahrazujícím pozadí bitmapy. Pozadí zdrojové bitmapy je definováno jako jeho bílé obrazové body a všechny obrazové body odpovídající barvě obrazového bodu v levém horním rohu bitmapy.

![Porovnání roztírených a původních verzí ikon](../../mfc/reference/media/vcditheredbitmap.gif "Porovnání roztírených a původních verzí ikon")

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="afxgetditheredbitmap"></a><a name="afxgetditheredbitmap"></a>AfxGetDitheredBitmap

Zkopíruje bitmapu a nahradí její pozadí rozkladem (šachovním) vzorkem.

```cpp
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Zdrojová bitmapa.

*pDest*<br/>
Cílová bitmapa.

*cr1*<br/>
Jedna ze dvou barev rozpisu barev, typicky bílá.

*cr2*<br/>
Další barva rozpisu barev, obvykle světle šedá (COLOR_MENU).

### <a name="remarks"></a>Poznámky

Zdrojová bitmapa se zkopíruje do cílové bitmapy s dvoubarevným *(cr1* a *cr2)* šachovným vzorkem nahrazujícím pozadí zdrojové bitmapy. Pozadí zdrojové bitmapy je definováno jako jeho bílé obrazové body a všechny obrazové body odpovídající barvě obrazového bodu v levém horním rohu bitmapy.

![Porovnání roztírených a původních verzí ikon](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
