---
title: Cmfcimagepaintarea – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::GetMode
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetBitmap
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetColor
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetMode
helpviewer_keywords:
- CMFCImagePaintArea [MFC], CMFCImagePaintArea
- CMFCImagePaintArea [MFC], GetMode
- CMFCImagePaintArea [MFC], SetBitmap
- CMFCImagePaintArea [MFC], SetColor
- CMFCImagePaintArea [MFC], SetMode
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
ms.openlocfilehash: 37d975ace4d144cc6274b49a3406382f0fb300ee
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290740"
---
# <a name="cmfcimagepaintarea-class"></a>Cmfcimagepaintarea – třída

Poskytuje oblast obrázku, který můžete použít ke změně obrázku v dialogovém okně editor obrázků.

## <a name="syntax"></a>Syntaxe

```
class CMFCImagePaintArea : public CButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|[CMFCImagePaintArea::CMFCImagePaintArea](#cmfcimagepaintarea)|Vytvoří `CMFCImagePaintArea` objektu.|
|`CMFCImagePaintArea::~CMFCImagePaintArea`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CMFCImagePaintArea::GetMode](#getmode)|Načte aktuální režim vykreslování.|
|[CMFCImagePaintArea::SetBitmap](#setbitmap)|Nastavuje rastrový obrázek pro oblasti obrázku.|
|[CMFCImagePaintArea::SetColor](#setcolor)|Nastaví aktuální vykreslení barvy.|
|[CMFCImagePaintArea::SetMode](#setmode)|Nastaví aktuální režim vykreslování.|

### <a name="remarks"></a>Poznámky

Tato třída není určena pro použití přímo v kódu.

Rozhraní používá tuto třídu pro zobrazení oblasti obrázku v dialogovém okně editor obrázků. Další informace o dialogové okno editoru obrázků, naleznete v tématu [CMFCImageEditorDialog – třída](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCImagePaintArea` třídy, nastavte aktuální vykreslení barvy, nastavte aktuální režim vykreslování a nastavte rastrový obrázek pro oblasti obrázku.

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afximagepaintarea.h

##  <a name="cmfcimagepaintarea"></a>  CMFCImagePaintArea::CMFCImagePaintArea

Vytvoří `CMFCImagePaintArea` objektu.

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pParentDlg*|[in] Ukazatel na dialogovém okně, které je nadřazené editoru obrázků.|

##  <a name="getmode"></a>  CMFCImagePaintArea::GetMode

Načte aktuální režim vykreslování.

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>Návratová hodnota

[IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) hodnotu, která určuje aktuální režim vykreslování.

##  <a name="setbitmap"></a>  CMFCImagePaintArea::SetBitmap

Nastavuje rastrový obrázek pro oblasti obrázku.

```
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pBitmap*|[in] Nový rastrový obrázek k zobrazení.|

### <a name="remarks"></a>Poznámky

Pokud *pBitmap* má hodnotu NULL, tato metoda nastaví velikost oblasti lze měnit barvy na nulu. Jinak nastaví velikost oblasti upravitelná malířského velikost zadaná rastrový obrázek.

##  <a name="setcolor"></a>  CMFCImagePaintArea::SetColor

Nastaví aktuální vykreslení barvy.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*color*|[in] Nové vykreslení barvy.|

### <a name="remarks"></a>Poznámky

Když vyberte barvu z palety panelu editor image nebo výběr barev, rozhraní volá tuto metodu za účelem aktualizace aktuální vykreslení barvy. Počáteční barva vykreslování je černá (COLORREF hodnotu 0).

Dialogové okno editor obrázků pro kreslení režimy všechny s výjimkou IMAGE_EDIT_MODE_COLOR používá vykreslení barvy. Další informace o vykreslování režimech najdete v tématu [cmfcimagepaintarea::image_edit_mode – výčet](cmfcimagepaintarea-image-edit-mode-enumeration.md).

##  <a name="setmode"></a>  CMFCImagePaintArea::SetMode

Nastaví aktuální režim vykreslování.

```
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*Režim*|[in] [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) hodnotu, která určuje aktuální režim vykreslování.|

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog – třída](../../mfc/reference/cmfcimageeditordialog-class.md)
