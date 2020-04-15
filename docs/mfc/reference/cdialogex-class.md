---
title: Třída CDialogEx
ms.date: 11/04/2016
f1_keywords:
- CDialogEx
- AFXDIALOGEX/CDialogEx
- AFXDIALOGEX/CDialogEx::CDialogEx
- AFXDIALOGEX/CDialogEx::SetBackgroundColor
- AFXDIALOGEX/CDialogEx::SetBackgroundImage
helpviewer_keywords:
- CDialogEx [MFC], CDialogEx
- CDialogEx [MFC], SetBackgroundColor
- CDialogEx [MFC], SetBackgroundImage
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
ms.openlocfilehash: b34c441ac63b023ae6272a1646151aad4be1bfbc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375638"
---
# <a name="cdialogex-class"></a>Třída CDialogEx

Třída `CDialogEx` určuje barvu pozadí a obrázek pozadí dialogového okna.

## <a name="syntax"></a>Syntaxe

```
class CDialogEx : public CDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CDialogEx::CDialogEx](#cdialogex)|Vytvoří `CDialogEx` objekt.|
|`CDialogEx::~CDialogEx`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDialogex::SetBackgroundColor](#setbackgroundcolor)|Nastaví barvu pozadí dialogového okna.|
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|Nastaví obrázek pozadí dialogového okna.|

## <a name="remarks"></a>Poznámky

Chcete-li `CDialogEx` použít třídu, odvodit třídu dialogového `CDialogEx` okna z třídy namísto třídy. `CDialog`

Obrázky dialogového okna jsou uloženy v souboru prostředků. Rozhraní framework automaticky odstraní všechny bitové kopie, která je načtena ze souboru prostředků. Chcete-li programově odstranit aktuální obrázek pozadí, zavolejte metodu [CDialogEx::SetBackgroundImage](#setbackgroundimage) nebo implementujte obslužnou rutinu `OnDestroy` události. Při volání [CDialogEx::SetBackgroundImage](#setbackgroundimage) metoda, předat `HBITMAP` parametr jako popisovač obrazu. Objekt `CDialogEx` převezme vlastnictví obrázku a odstraní `m_bAutoDestroyBmp` jej, `TRUE`pokud je příznak .

Objekt `CDialogEx` může být nadřazený objekt [třídy CMFCPopupMenu.](../../mfc/reference/cmfcpopupmenu-class.md) Objekt [TŘÍDY CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) volá metodu `CDialogEx::SetActiveMenu` při otevření objektu [třídy CMFCPopupMenu.](../../mfc/reference/cmfcpopupmenu-class.md) Poté `CDialogEx` objekt zpracovává všechny události nabídky, dokud [cmFCPopupMenu třídy](../../mfc/reference/cmfcpopupmenu-class.md) objektu je uzavřen.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxDialogex.h

## <a name="cdialogexcdialogex"></a><a name="cdialogex"></a>CDialogEx::CDialogEx

Vytvoří `CDialogEx` objekt.

```
CDialogEx(
    UINT nIDTemplate,
    CWnd* pParent=NULL);

CDialogEx(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd=NULL);
```

### <a name="parameters"></a>Parametry

*nIDŠablona*<br/>
[v] ID prostředku šablony dialogového okna.

*lpszTemplateName*<br/>
[v] Název prostředku šablony dialogového okna.

*pParent*<br/>
[v] Ukazatel na nadřazené okno. Výchozí hodnota je NULL.

*pParentWnd*<br/>
[v] Ukazatel na nadřazené okno. Výchozí hodnota je NULL.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdialogexsetbackgroundcolor"></a><a name="setbackgroundcolor"></a>CDialogex::SetBackgroundColor

Nastaví barvu pozadí dialogového okna.

```
void SetBackgroundColor(
    COLORREF color,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[v] Hodnota barvy RGB.

*bPřekreslit*<br/>
[v] TRUE okamžitě aktualizovat obrazovku; jinak NEPRAVDA. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

## <a name="cdialogexsetbackgroundimage"></a><a name="setbackgroundimage"></a>CDialogEx::SetBackgroundImage

Nastaví obrázek pozadí dialogového okna.

```
void SetBackgroundImage(
    HBITMAP hBitmap,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bAutoDestroy=TRUE,
    BOOL bRepaint=TRUE);

BOOL SetBackgroundImage(
    UINT uiBmpResId,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
[v] Úchyt k obrázku pozadí.

*uiBmpResId*<br/>
[v] ID prostředku obrázku na pozadí.

*Umístění*<br/>
[v] Jedna z `CDialogEx::BackgroundLocation` hodnot, které určují umístění obrazu. Mezi platné hodnoty patří BACKGR_TILE, BACKGR_TOPLEFT, BACKGR_TOPRIGHT, BACKGR_BOTTOMLEFT a BACKGR_BOTTOMRIGHT. Výchozí hodnota je BACKGR_TILE.

*bAutoDestroy*<br/>
[v] TRUE automaticky zničit obrázek na pozadí; jinak NEPRAVDA.

*bPřekreslit*<br/>
[v] TRUE pro okamžité překreslení dialogového okna; jinak NEPRAVDA.

### <a name="return-value"></a>Návratová hodnota

V syntaxi přetížení druhé metody TRUE, pokud je metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Zadaná bitová kopie není roztažená tak, aby se vešla do klientské oblasti dialogového okna.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída cmfcpopupmenu](../../mfc/reference/cmfcpopupmenu-class.md)<br/>
[Třída CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)
