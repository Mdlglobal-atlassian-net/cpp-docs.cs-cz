---
title: Cmfctabdroptarget – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragEnter
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragLeave
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragOver
- AFXBASETABCTRL/CMFCTabDropTarget::OnDropEx
- AFXBASETABCTRL/CMFCTabDropTarget::Register
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabDropTarget [MFC], OnDragEnter
- CMFCTabDropTarget [MFC], OnDragLeave
- CMFCTabDropTarget [MFC], OnDragOver
- CMFCTabDropTarget [MFC], OnDropEx
- CMFCTabDropTarget [MFC], Register
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5f4951da1f6407dae1d31d92724bbcc80e677616
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442432"
---
# <a name="cmfctabdroptarget-class"></a>Cmfctabdroptarget – třída

Poskytuje mechanismus pro komunikaci mezi ovládacím prvkem karta a knihovnami OLE.

## <a name="syntax"></a>Syntaxe

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|`CMFCTabDropTarget::CMFCTabDropTarget`|Výchozí konstruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|Volá se rozhraním, když uživatel přetáhne objekt do okna Karta. (Přepíše [COleDropTarget::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|Volá se rozhraním, když uživatel přetáhne objekt mimo časové období kartu, která má fokus. (Přepíše [COleDropTarget::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|
|[CMFCTabDropTarget::OnDragOver](#ondragover)|Volá se rozhraním, když uživatel přetáhne objektu na kartě okna, který má právě fokus. (Přepíše [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|
|[CMFCTabDropTarget::OnDropEx](#ondropex)|Volá se rozhraním, když uživatel uvolní tlačítko myši na konci operace přetažení. (Přepíše [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).)|
|[CMFCTabDropTarget::Register](#register)|Ovládací prvek se zaregistruje jako ten, který může sloužit jako cíl operace přetažení myší OLE.|

### <a name="remarks"></a>Poznámky

Tato třída podporuje přetahování myší `CMFCBaseTabCtrl` třídy. Pokud vaše aplikace inicializuje s použitím knihovny OLE [AfxOleInit](ole-initialization.md#afxoleinit) funkci `CMFCBaseTabCtrl` objekty zaregistrovat pro operace a přetažení.

`CMFCTabDropTarget` Třída rozšiřuje své základní třídy tak, že na kartě, které je pod kurzor, když dojde k operaci přetažení aktivní. Další informace týkající se operací přetažení myší, naleznete v tématu [oblast pro přetažení přetažení (OLE)](../../mfc/drag-and-drop-ole.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `CMFCTabDropTarget` objektu a použít jeho `Register` metoda.

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[Coledroptarget –](../../mfc/reference/coledroptarget-class.md)

[Cmfctabdroptarget –](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxbasetabctrl.h

##  <a name="ondragenter"></a>  CMFCTabDropTarget::OnDragEnter

Volá se rozhraním, když uživatel přetáhne objekt do okna Karta.

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
|*pWnd*|[in] Nevyužité.|
|*pDataObject*|[in] Ukazatel na objekt, který uživatel přetáhne.|
|*dwKeyState*|[in] Obsahuje informace o stavu modifikační klávesy. Jedná se o kombinaci libovolný počet následující: MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.|
|*Bod*|[in] Umístění kurzoru v souřadnicích klienta.|

### <a name="return-value"></a>Návratová hodnota

Efekt, který je výsledkem v případě v místě určeném v rozevíracím *bodu*. Může být jeden nebo více z následujících akcí:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Poznámky

Tato metoda vrátí DROPEFFECT_NONE, pokud není v režimu vlastního nastavení rozhraní nástrojů nebo formát dat schránky není k dispozici. V opačném případě vrátí výsledek volání `CMFCBaseTabCtrl::OnDragEnter` pomocí zadaných parametrů.

Další informace o režimu přizpůsobení, najdete v části [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Další informace o formátech dat schránky najdete v tématu [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

##  <a name="ondragleave"></a>  CMFCTabDropTarget::OnDragLeave

Volá se rozhraním, když uživatel přetáhne objekt mimo časové období kartu, která má fokus.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pWnd*|[in] Nevyužité.|

### <a name="remarks"></a>Poznámky

Tato metoda volá `CMFCBaseTabCtrl::OnDragLeave` metody k provedení operace přetažení.

##  <a name="ondragover"></a>  CMFCTabDropTarget::OnDragOver

Volá se rozhraním, když uživatel přetáhne objektu na kartě okna, který má právě fokus.

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
|*pWnd*|[in] Nevyužité.|
|*pDataObject*|[in] Ukazatel na objekt, který uživatel přetáhne.|
|*dwKeyState*|[in] Obsahuje informace o stavu modifikační klávesy. Jedná se o kombinaci libovolný počet následující: MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.|
|*Bod*|[in] Umístění ukazatele myši v souřadnice klienta.|

### <a name="return-value"></a>Návratová hodnota

Efekt, který je výsledkem v případě v místě určeném v rozevíracím *bodu*. Může být jeden nebo více z následujících akcí:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Poznámky

Tato metoda provádí kartu, která je pod kurzorem při výskytu aktivní operace přetažení. Vrátí DROPEFFECT_NONE, pokud není v režimu vlastního nastavení rozhraní nástrojů nebo formát dat schránky není k dispozici. V opačném případě vrátí výsledek volání `CMFCBaseTabCtrl::OnDragOver` pomocí zadaných parametrů.

Další informace o režimu přizpůsobení, najdete v části [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Další informace o formátech dat schránky najdete v tématu [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

##  <a name="ondropex"></a>  CMFCTabDropTarget::OnDropEx

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
|*pWnd*|[in] Nevyužité.|
|*pDataObject*|[in] Ukazatel na objekt, který uživatel přetáhne.|
|*dropEffect*|[in] Výchozí operaci přetažení.|
|*rozevíracího seznamu*|[in] Nevyužité.|
|*Bod*|[in] Umístění ukazatele myši v souřadnice klienta.|

### <a name="return-value"></a>Návratová hodnota

Výsledný efekt přetažení. Může být jeden nebo více z následujících akcí:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Poznámky

Tato metoda volá `CMFCBaseTabCtrl::OnDrop` Pokud rozhraní nástrojů je v režimu vlastního nastavení a formát dat schránky je k dispozici. Pokud volání `CMFCBaseTabCtrl::OnDrop` vrátí nenulovou hodnotu, tato metoda vrátí výchozí odkládací efekt určené *dropEffect*. V opačném případě vrátí tato metoda DROPEFFECT_NONE. Další informace o rozevírací efektů, naleznete v tématu [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).

Další informace o režimu přizpůsobení, najdete v části [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Další informace o formátech dat schránky najdete v tématu [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

##  <a name="register"></a>  CMFCTabDropTarget::Register

Ovládací prvek se zaregistruje jako ten, který může sloužit jako cíl operace přetažení myší OLE.

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pOwner*|[in] Ovládací prvek karty zaregistrovat jako cíl přetažení.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla registrace úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda volá [COleDropTarget::Register](../../mfc/reference/coledroptarget-class.md#register) zaregistrovat ovládací prvky pro operace a přetažení.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Přetažení (OLE)](../../mfc/drag-and-drop-ole.md)



