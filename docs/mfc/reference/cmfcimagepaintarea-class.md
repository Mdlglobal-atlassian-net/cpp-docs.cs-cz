---
title: CMFCImagePaintArea – třída
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
ms.openlocfilehash: cd74d2418bb874553fbbafa637f527a7b84b73bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754281"
---
# <a name="cmfcimagepaintarea-class"></a>CMFCImagePaintArea – třída

Poskytuje oblast obrázku, kterou používáte k úpravě obrazu v dialogovém okně editoru obrázků.

## <a name="syntax"></a>Syntaxe

```
class CMFCImagePaintArea : public CButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|[CMFCImagePaintArea::CMFCImagePaintArea](#cmfcimagepaintarea)|Vytvoří `CMFCImagePaintArea` objekt.|
|`CMFCImagePaintArea::~CMFCImagePaintArea`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CMFCImagePaintArea::GetMode](#getmode)|Načte aktuální režim výkresu.|
|[CMFCImagePaintArea::SetBitmap](#setbitmap)|Nastaví bitmapový obraz pro oblast obrázku.|
|[CMFCImagePaintarea::SetColor](#setcolor)|Nastaví aktuální barvu výkresu.|
|[CMFCImagePaintArea::SetMode](#setmode)|Nastaví aktuální režim kreslení.|

### <a name="remarks"></a>Poznámky

Tato třída není určena pro použití přímo z vašeho kódu.

Rozhraní framework používá tuto třídu k zobrazení oblasti obrázku v dialogovém okně editoru obrázků. Další informace o dialogovém okně editoru obrázků naleznete v tématu [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCImagePaintArea` třídy, nastavit aktuální barvu výkresu, nastavit aktuální režim kreslení a nastavit bitmapový obraz pro oblast obrázku.

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afximagepaintarea.h

## <a name="cmfcimagepaintareacmfcimagepaintarea"></a><a name="cmfcimagepaintarea"></a>CMFCImagePaintArea::CMFCImagePaintArea

Vytvoří `CMFCImagePaintArea` objekt.

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pParentDlg*|[v] Ukazatel na dialogové okno, které je nadřazenou položkou editoru obrázků.|

## <a name="cmfcimagepaintareagetmode"></a><a name="getmode"></a>CMFCImagePaintArea::GetMode

Načte aktuální režim výkresu.

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota [IMAGE_EDIT_MODE,](cmfcimagepaintarea-image-edit-mode-enumeration.md) která určuje aktuální režim výkresu.

## <a name="cmfcimagepaintareasetbitmap"></a><a name="setbitmap"></a>CMFCImagePaintArea::SetBitmap

Nastaví bitmapový obraz pro oblast obrázku.

```cpp
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pBitmap*|[v] Nový bitmapový obraz, který se má zobrazit.|

### <a name="remarks"></a>Poznámky

Pokud *pBitmap* je NULL, tato metoda nastaví velikost upravitelné oblasti malování na nulu. V opačném případě nastaví velikost upravitelné oblasti malby na velikost poskytnutého bitmapového obrazu.

## <a name="cmfcimagepaintareasetcolor"></a><a name="setcolor"></a>CMFCImagePaintarea::SetColor

Nastaví aktuální barvu výkresu.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*color*|[v] Nová barva výkresu.|

### <a name="remarks"></a>Poznámky

Když vyberete barvu z panelu palety editoru obrázků nebo výběru barev, rozhraní framework zavolá tuto metodu k aktualizaci aktuální barvy výkresu. Počáteční barva výkresu je černá (hodnota COLORREF 0).

Barva výkresu je používána v dialogovém okně editoru obrázků pro všechny režimy kreslení s výjimkou IMAGE_EDIT_MODE_COLOR. Další informace o režimech kreslení naleznete v tématu [CMFCImagePaintArea::IMAGE_EDIT_MODE Výčet](cmfcimagepaintarea-image-edit-mode-enumeration.md).

## <a name="cmfcimagepaintareasetmode"></a><a name="setmode"></a>CMFCImagePaintArea::SetMode

Nastaví aktuální režim kreslení.

```cpp
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*Režimu*|[v] Hodnota [IMAGE_EDIT_MODE,](cmfcimagepaintarea-image-edit-mode-enumeration.md) která určuje aktuální režim výkresu.|

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog – třída](../../mfc/reference/cmfcimageeditordialog-class.md)
