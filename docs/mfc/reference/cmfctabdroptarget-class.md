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
ms.openlocfilehash: 83432fdb90fe28214fb1faaf843556deb2f44750
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367347"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget – třída

Poskytuje mechanismus komunikace mezi ovládacím prvkem tabulátoru a knihovnami OLE.

## <a name="syntax"></a>Syntaxe

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Name (Název)|Popis|
|`CMFCTabDropTarget::CMFCTabDropTarget`|Výchozí konstruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Name (Název)|Popis|
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|Volat rámci při uživatel přetáhne objekt do okna karty. (Přepíše [COleDropTarget::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|
|[CMFCtabdroptarget::ondragleave](#ondragleave)|Volat rámci při uživatel přetáhne objekt mimo okno karty, která má fokus. (Přepíše [COleDropTarget::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|
|[CMFCTabDropTarget::OnDragover](#ondragover)|Volat rámci při uživatel přetáhne objekt na kartu okna, které má fokus. (Přepíše [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|
|[CMFCtabdroptarget::OnDropEx](#ondropex)|Volat rámci při uživatel uvolní tlačítko myši na konci operace přetažení. (Přepíše [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).)|
|[CMFCTabDropTarget::Registrovat](#register)|Registruje ovládací prvek jako ten, který může být cílem operace ole přetažení myší.|

### <a name="remarks"></a>Poznámky

Tato třída poskytuje podporu přetažení `CMFCBaseTabCtrl` třídy. Pokud aplikace inicializuje knihovny OLE pomocí funkce [AfxOleInit,](ole-initialization.md#afxoleinit) `CMFCBaseTabCtrl` objekty se zaregistrují pro operace přetažení myší.

Třída `CMFCTabDropTarget` rozšiřuje svou základní třídu tím, že karta, která je pod kurzorem, když dojde k operaci přetažení aktivní. Další informace o operacích přetažení myší naleznete v tématu [OLE drag and drop](../../mfc/drag-and-drop-ole.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCTabDropTarget` vytvořit objekt `Register` a použít jeho metodu.

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxbasetabctrl.h

## <a name="cmfctabdroptargetondragenter"></a><a name="ondragenter"></a>CMFCTabDropTarget::OnDragEnter

Volat rámci při uživatel přetáhne objekt do okna karty.

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
|*pWnd*|[v] Nepoužité.|
|*objekt pDataObject*|[v] Ukazatel na objekt, který uživatel přetáhne.|
|*dwKeyState*|[v] Obsahuje stav modifikačních klíčů. Jedná se o kombinaci libovolného počtu: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.|
|*Bod*|[v] Umístění kurzoru v souřadnicích klienta.|

### <a name="return-value"></a>Návratová hodnota

Efekt, který vzniká, pokud dojde k poklesu v umístění určeném *bodem*. Může to být jedna nebo více z následujících možností:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Poznámky

Tato metoda vrátí DROPEFFECT_NONE pokud rozhraní panelu nástrojů není v režimu přizpůsobení nebo je datový formát schránky nedostupný. V opačném případě vrátí `CMFCBaseTabCtrl::OnDragEnter` výsledek volání s zadanými parametry.

Další informace o režimu vlastního nastavení naleznete v tématu [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Další informace o datových formátech schránky naleznete v tématu [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondragleave"></a><a name="ondragleave"></a>CMFCtabdroptarget::ondragleave

Volat rámci při uživatel přetáhne objekt mimo okno karty, která má fokus.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pWnd*|[v] Nepoužité.|

### <a name="remarks"></a>Poznámky

Tato metoda `CMFCBaseTabCtrl::OnDragLeave` volá metodu k provedení operace přetažení.

## <a name="cmfctabdroptargetondragover"></a><a name="ondragover"></a>CMFCTabDropTarget::OnDragover

Volat rámci při uživatel přetáhne objekt na kartu okna, které má fokus.

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
|*pWnd*|[v] Nepoužité.|
|*objekt pDataObject*|[v] Ukazatel na objekt, který uživatel přetáhne.|
|*dwKeyState*|[v] Obsahuje stav modifikačních klíčů. Jedná se o kombinaci libovolného počtu: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.|
|*Bod*|[v] Umístění ukazatele myši v souřadnicích klienta.|

### <a name="return-value"></a>Návratová hodnota

Efekt, který vzniká, pokud dojde k poklesu v umístění určeném *bodem*. Může to být jedna nebo více z následujících možností:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Poznámky

Tato metoda umožňuje kartu, která je pod kurzorem, když dojde k operaci přetažení aktivní. Vrátí DROPEFFECT_NONE pokud rozhraní panelu nástrojů není v režimu přizpůsobení nebo je datový formát schránky nedostupný. V opačném případě vrátí `CMFCBaseTabCtrl::OnDragOver` výsledek volání s zadanými parametry.

Další informace o režimu vlastního nastavení naleznete v tématu [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Další informace o datových formátech schránky naleznete v tématu [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondropex"></a><a name="ondropex"></a>CMFCtabdroptarget::OnDropEx

Volat rámci při uživatel uvolní tlačítko myši na konci operace přetažení.

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
|*pWnd*|[v] Nepoužité.|
|*objekt pDataObject*|[v] Ukazatel na objekt, který uživatel přetáhne.|
|*efekt přetažení*|[v] Výchozí operace přetažení.|
|*dropList*|[v] Nepoužité.|
|*Bod*|[v] Umístění ukazatele myši v souřadnicích klienta.|

### <a name="return-value"></a>Návratová hodnota

Výsledný efekt přetažení. Může to být jedna nebo více z následujících možností:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Poznámky

Tato metoda `CMFCBaseTabCtrl::OnDrop` volá, pokud je rozhraní panelu nástrojů v režimu přizpůsobení a je k dispozici formát dat schránky. Pokud volání `CMFCBaseTabCtrl::OnDrop` vrátí nenulovou hodnotu, vrátí tato metoda výchozí efekt přetažení určený *parametrem dropEffect*. Jinak tato metoda vrátí DROPEFFECT_NONE. Další informace o efektech přetažení naleznete v tématu [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).

Další informace o režimu vlastního nastavení naleznete v tématu [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Další informace o datových formátech schránky naleznete v tématu [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetregister"></a><a name="register"></a>CMFCTabDropTarget::Registrovat

Registruje ovládací prvek jako ten, který může být cílem operace ole přetažení myší.

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pVlastník*|[v] Ovládací prvek karta zaregistrovat jako cíl přetažení.|

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla registrace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda volá [COleDropTarget::Register](../../mfc/reference/coledroptarget-class.md#register) zaregistrovat ovládací prvek pro operace přetažení myší.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[OLE – přetažení](../../mfc/drag-and-drop-ole.md)
