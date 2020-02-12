---
title: CMFCTabDropTarget – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragEnter
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragLeave
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragOver
- AFXBASETABCTRL/CMFCTabDropTarget::OnDropEx
- AFXBASETABCTRL/CMFCTabDropTarget::Register
helpviewer_keywords:
- CMFCTabDropTarget [MFC], OnDragEnter
- CMFCTabDropTarget [MFC], OnDragLeave
- CMFCTabDropTarget [MFC], OnDragOver
- CMFCTabDropTarget [MFC], OnDropEx
- CMFCTabDropTarget [MFC], Register
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
ms.openlocfilehash: d0090386b1ebb4d89b9a7613a0b2a28529decbe5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127425"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget – třída

Poskytuje komunikační mechanismus mezi ovládacím prvkem karta a knihovnami OLE.

## <a name="syntax"></a>Syntaxe

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|`CMFCTabDropTarget::CMFCTabDropTarget`|Výchozí konstruktor|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|Volá se rozhraním, když uživatel přetáhne objekt do okna karty. (Overrides [COleDropTarget:: OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|Volá se rozhraním, když uživatel přetáhne objekt mimo okno karty, které má fokus. (Overrides [COleDropTarget:: OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|
|[CMFCTabDropTarget::OnDragOver](#ondragover)|Volá se rozhraním, když uživatel přetáhne objekt na okno karty, které má fokus. (Overrides [COleDropTarget:: OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|
|[CMFCTabDropTarget::OnDropEx](#ondropex)|Volá se rozhraním, když uživatel uvolní tlačítko myši na konci operace přetažení. (Overrides [COleDropTarget:: OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).)|
|[CMFCTabDropTarget:: Register](#register)|Registruje ovládací prvek jako ten, který může být cílem operace přetažení OLE.|

### <a name="remarks"></a>Poznámky

Tato třída poskytuje podporu přetažení pro třídu `CMFCBaseTabCtrl`. Pokud vaše aplikace inicializuje knihovny OLE pomocí funkce [AfxOleInit](ole-initialization.md#afxoleinit) , `CMFCBaseTabCtrl` objekty, které se registrují pro operace přetažení.

Třída `CMFCTabDropTarget` rozšiřuje svou základní třídu tím, že při aktivní operaci přetažení vykoná kartu, která je pod kurzorem. Další informace o operacích přetažení najdete v tématu přetažení [OLE](../../mfc/drag-and-drop-ole.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCTabDropTarget` a použít jeho metodu `Register`.

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxbasetabctrl. h

##  <a name="ondragenter"></a>CMFCTabDropTarget::OnDragEnter

Volá se rozhraním, když uživatel přetáhne objekt do okna karty.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pWnd*|pro Nepoužívané.|
|*pDataObject*|pro Ukazatel na objekt, který uživatel přetáhne.|
|*dwKeyState*|pro Obsahuje stav modifikačních kláves. Jedná se o kombinaci libovolného počtu následujících: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.|
|*Vyberte*|pro Umístění kurzoru v souřadnicích klienta.|

### <a name="return-value"></a>Návratová hodnota

Výsledek, který je výsledkem, pokud dojde k přerušení v umístění určeném *bodem*. Může to být jedna nebo víc z těchto možností:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Poznámky

Tato metoda vrací DROPEFFECT_NONE, pokud není rozhraní panelu nástrojů v režimu přizpůsobení nebo není k dispozici formát dat ve schránce. V opačném případě vrátí výsledek volání `CMFCBaseTabCtrl::OnDragEnter` se zadanými parametry.

Další informace o režimu přizpůsobení naleznete v tématu [CMFCToolBar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Další informace o formátech dat ve schránce najdete v tématu [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

##  <a name="ondragleave"></a>CMFCTabDropTarget::OnDragLeave

Volá se rozhraním, když uživatel přetáhne objekt mimo okno karty, které má fokus.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pWnd*|pro Nepoužívané.|

### <a name="remarks"></a>Poznámky

Tato metoda volá metodu `CMFCBaseTabCtrl::OnDragLeave` k provedení operace přetažení.

##  <a name="ondragover"></a>CMFCTabDropTarget::OnDragOver

Volá se rozhraním, když uživatel přetáhne objekt na okno karty, které má fokus.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pWnd*|pro Nepoužívané.|
|*pDataObject*|pro Ukazatel na objekt, který uživatel přetáhne.|
|*dwKeyState*|pro Obsahuje stav modifikačních kláves. Jedná se o kombinaci libovolného počtu následujících: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.|
|*Vyberte*|pro Umístění ukazatele myši v souřadnicích klienta.|

### <a name="return-value"></a>Návratová hodnota

Výsledek, který je výsledkem, pokud dojde k přerušení v umístění určeném *bodem*. Může to být jedna nebo víc z těchto možností:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří kartu, která je pod kurzorem, když dojde k operaci přetažení aktivní. Vrátí DROPEFFECT_NONE, pokud není rozhraní panelu nástrojů v režimu přizpůsobení nebo není k dispozici formát dat ve schránce. V opačném případě vrátí výsledek volání `CMFCBaseTabCtrl::OnDragOver` se zadanými parametry.

Další informace o režimu přizpůsobení naleznete v tématu [CMFCToolBar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Další informace o formátech dat ve schránce najdete v tématu [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

##  <a name="ondropex"></a>CMFCTabDropTarget::OnDropEx

Volá se rozhraním, když uživatel uvolní tlačítko myši na konci operace přetažení.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pWnd*|pro Nepoužívané.|
|*pDataObject*|pro Ukazatel na objekt, který uživatel přetáhne.|
|*dropEffect*|pro Výchozí operace drop.|
|*Seznamu*|pro Nepoužívané.|
|*Vyberte*|pro Umístění ukazatele myši v souřadnicích klienta.|

### <a name="return-value"></a>Návratová hodnota

Výsledný efekt zrušení. Může to být jedna nebo víc z těchto možností:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Poznámky

Tato metoda volá `CMFCBaseTabCtrl::OnDrop`, pokud je rozhraní panelu nástrojů v režimu přizpůsobení a je k dispozici formát dat ve schránce. Pokud volání `CMFCBaseTabCtrl::OnDrop` vrátí nenulovou hodnotu, vrátí tato metoda výchozí efekt odtažení určený parametrem *DROPEFFECT*. V opačném případě vrátí tato metoda DROPEFFECT_NONE. Další informace o účincích přetažení naleznete v tématu [COleDropTarget:: OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).

Další informace o režimu přizpůsobení naleznete v tématu [CMFCToolBar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Další informace o formátech dat ve schránce najdete v tématu [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

##  <a name="register"></a>CMFCTabDropTarget:: Register

Registruje ovládací prvek jako ten, který může být cílem operace přetažení OLE.

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pOwner*|pro Ovládací prvek karta, který se má zaregistrovat jako cíl přetažení|

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla registrace úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato metoda volá [COleDropTarget:: Register](../../mfc/reference/coledroptarget-class.md#register) pro registraci ovládacího prvku pro operace přetažení.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[OLE – přetažení](../../mfc/drag-and-drop-ole.md)
