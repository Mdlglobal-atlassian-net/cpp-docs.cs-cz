---
title: COleDropTarget Class
ms.date: 11/04/2016
f1_keywords:
- COleDropTarget
- AFXOLE/COleDropTarget
- AFXOLE/COleDropTarget::COleDropTarget
- AFXOLE/COleDropTarget::OnDragEnter
- AFXOLE/COleDropTarget::OnDragLeave
- AFXOLE/COleDropTarget::OnDragOver
- AFXOLE/COleDropTarget::OnDragScroll
- AFXOLE/COleDropTarget::OnDrop
- AFXOLE/COleDropTarget::OnDropEx
- AFXOLE/COleDropTarget::Register
- AFXOLE/COleDropTarget::Revoke
helpviewer_keywords:
- COleDropTarget [MFC], COleDropTarget
- COleDropTarget [MFC], OnDragEnter
- COleDropTarget [MFC], OnDragLeave
- COleDropTarget [MFC], OnDragOver
- COleDropTarget [MFC], OnDragScroll
- COleDropTarget [MFC], OnDrop
- COleDropTarget [MFC], OnDropEx
- COleDropTarget [MFC], Register
- COleDropTarget [MFC], Revoke
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
ms.openlocfilehash: 127245385ebd89e51a1cc77d1efaa16729d73fe7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300116"
---
# <a name="coledroptarget-class"></a>COleDropTarget Class

Poskytuje mechanismus pro komunikaci mezi oknem a knihovnami OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDropTarget : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleDropTarget::COleDropTarget](#coledroptarget)|Vytvoří `COleDropTarget` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleDropTarget::OnDragEnter](#ondragenter)|Volá se, když ukazatel poprvé vstoupí do okna.|
|[COleDropTarget::OnDragLeave](#ondragleave)|Volá se, když ukazatel ocitne mimo okno.|
|[COleDropTarget::OnDragOver](#ondragover)|Volá se opakovaně, když se kurzor přesune na okno.|
|[COleDropTarget::OnDragScroll](#ondragscroll)|Voláno k určení, zda je kurzor přetáhnout do oblasti posuvníku okna.|
|[COleDropTarget::OnDrop](#ondrop)|Volá se, když data je přetáhnout do okna výchozí obslužnou rutinu.|
|[COleDropTarget::OnDropEx](#ondropex)|Volá se, když data je přetáhnout do okna počáteční obslužné rutiny.|
|[COleDropTarget::Register](#register)|V okně se zaregistruje jako cíl přetažení. platné.|
|[COleDropTarget::Revoke](#revoke)|Způsobí, že v okně přestanou se platný cíl.|

## <a name="remarks"></a>Poznámky

Vytvoření objektů této třídy umožňuje oknu tak, aby přijímal data pomocí mechanismu a přetahování OLE.

Získat okna tak, aby přijímal příkazů drop, byste nejprve vytvořit objekt `COleDropTarget` třídy a následně zavolat [zaregistrovat](#register) funkce s ukazatelem na požadovaný `CWnd` objektu jako jediný parametr.

Další informace o operací přetažení myší pomocí OLE, najdete v článku [oblast pro přetažení přetažení (OLE)](../../mfc/drag-and-drop-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

##  <a name="coledroptarget"></a>  COleDropTarget::COleDropTarget

Vytvoří objekt třídy `COleDropTarget`.

```
COleDropTarget();
```

### <a name="remarks"></a>Poznámky

Volání [zaregistrovat](#register) má tento objekt přidružit časového období.

##  <a name="ondragenter"></a>  COleDropTarget::OnDragEnter

Volá se rozhraním, když je kurzor nejprve přetáhnout do okna.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Vstupující body v okně kurzor.

*pDataObject*<br/>
Odkazuje na datový objekt, který obsahuje data, která se dá přetáhnout.

*dwKeyState*<br/>
Obsahuje informace o stavu modifikační klávesy. Jedná se o kombinaci libovolný počet následující: MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*point*<br/>
Obsahuje aktuální umístění kurzoru v souřadnicích klienta.

### <a name="return-value"></a>Návratová hodnota

O tom, že pokud přetažení došlo k pokusům v umístění určeném, by stálo *bodu*. Může být jeden nebo více z následujících akcí:

- Přetažení A DROPEFFECT_NONE nebude povolen.

- Operace kopírování A DROPEFFECT_COPY by byla prováděna.

- Operace přesunu A DROPEFFECT_MOVE by byla prováděna.

- Odkaz A DROPEFFECT_LINK z vyřazené dat na původní data by byla založena.

- DROPEFFECT_SCROLL A přetažením posuvníku operace se použije nebo dochází v cíli.

### <a name="remarks"></a>Poznámky

Přepsání této funkce můžete povolit operace přetažení vyskytuje v okně. Výchozí implementace volá [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), který jednoduše vrací DROPEFFECT_NONE ve výchozím nastavení.

Další informace najdete v tématu [IDropTarget::DragEnter](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragenter) v sadě Windows SDK.

##  <a name="ondragleave"></a>  COleDropTarget::OnDragLeave

Volá se rozhraním, když ukazatel opustí okna při přetahování operace je v platnosti.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Opouští body v okně kurzor.

### <a name="remarks"></a>Poznámky

Tato funkce přepište, pokud mají zvláštní chování při operaci přetažení opustí určené okno. Výchozí implementace této funkce se volá [CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).

Další informace najdete v tématu [IDropTarget::DragLeave](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragleave) v sadě Windows SDK.

##  <a name="ondragover"></a>  COleDropTarget::OnDragOver

Volá se rozhraním, když se kurzor přesune na okno.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Body okna, které se ukazatel myši nachází.

*pDataObject*<br/>
Odkazuje na datový objekt, který obsahuje data, která mají být vyřazeny.

*dwKeyState*<br/>
Obsahuje informace o stavu modifikační klávesy. Jedná se o kombinaci libovolný počet následující: MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*point*<br/>
Obsahuje aktuální umístění kurzoru v souřadnicích klienta.

### <a name="return-value"></a>Návratová hodnota

O tom, že pokud přetažení došlo k pokusům v umístění určeném, by stálo *bodu*. Může být jeden nebo více z následujících akcí:

- Přetažení A DROPEFFECT_NONE nebude povolen.

- Operace kopírování A DROPEFFECT_COPY by byla prováděna.

- Operace přesunu A DROPEFFECT_MOVE by byla prováděna.

- Odkaz A DROPEFFECT_LINK z vyřazené dat na původní data by byla založena.

- DROPEFFECT_SCROLL znamená, že operace přetažení posuvníku se použije nebo dochází v cíli.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být potlačena za účelem povolení operací přetažení vyskytuje v okně. Výchozí implementace této funkce se volá [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover), která vrací DROPEFFECT_NONE ve výchozím nastavení. Protože tato funkce je volána často během operace přetažení myší, to by mělo být optimalizované co největší míře.

Další informace najdete v tématu [IDropTarget::DragOver](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragover) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

##  <a name="ondragscroll"></a>  COleDropTarget::OnDragScroll

Volá se rozhraním před voláním [ondragenter –](#ondragenter) nebo [ondragover –](#ondragover) k určení, zda *bodu* v posuvné oblasti.

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, které se ukazatel myši momentálně nachází.

*dwKeyState*<br/>
Obsahuje informace o stavu modifikační klávesy. Jedná se o kombinaci libovolný počet následující: MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*point*<br/>
Obsahuje umístění kurzoru v pixelech, vzhledem k obrazovce.

### <a name="return-value"></a>Návratová hodnota

O tom, že pokud přetažení došlo k pokusům v umístění určeném, by stálo *bodu*. Může být jeden nebo více z následujících akcí:

- Přetažení A DROPEFFECT_NONE nebude povolen.

- Operace kopírování A DROPEFFECT_COPY by byla prováděna.

- Operace přesunu A DROPEFFECT_MOVE by byla prováděna.

- Odkaz A DROPEFFECT_LINK z vyřazené dat na původní data by byla založena.

- DROPEFFECT_SCROLL znamená, že operace přetažení posuvníku se použije nebo dochází v cíli.

### <a name="remarks"></a>Poznámky

Tato funkce přepište, pokud chcete zadat zvláštní chování pro tuto událost. Výchozí implementace této funkce se volá [CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), který vrátí DROPEFFECT_NONE a posune okno, když je kurzor přetáhnout do oblasti posuvníku výchozí uvnitř ohraničení okna.

##  <a name="ondrop"></a>  COleDropTarget::OnDrop

Volá se rozhraním, když operace přetažení, která se má použít.

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, které se ukazatel myši momentálně nachází.

*pDataObject*<br/>
Odkazuje na datový objekt, který obsahuje data, která mají být vyřazeny.

*dropEffect*<br/>
Efekt, který uživatel vybral pro operaci přetažení. Může být jeden nebo více z následujících akcí:

- Operace kopírování A DROPEFFECT_COPY by byla prováděna.

- Operace přesunu A DROPEFFECT_MOVE by byla prováděna.

- Odkaz A DROPEFFECT_LINK z vyřazené dat na původní data by byla založena.

*point*<br/>
Obsahuje umístění kurzoru v pixelech, vzhledem k obrazovce.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšné; rozevírací jinak 0.

### <a name="remarks"></a>Poznámky

První volání rozhraní framework [ondropex –](#ondropex). Pokud `OnDropEx` funkce nezpracovává rozevírací nabídku, rozhraní, zavolá tato členská funkce `OnDrop`. Obvykle aplikace přepíše [ondropex –](../../mfc/reference/cview-class.md#ondropex) ve třídě zobrazení zpracovat stisknutí pravého tlačítka myši přetáhnout myší. Obvykle třída zobrazení [OnDrop](../../mfc/reference/cview-class.md#ondrop) se používá ke zpracování jednoduché operace přetažení.

Výchozí implementace `COleDropTarget::OnDrop` volání [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop), který jednoduše vrací hodnotu FALSE ve výchozím nastavení.

Další informace najdete v tématu [IDropTarget::Drop](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-drop) v sadě Windows SDK.

##  <a name="ondropex"></a>  COleDropTarget::OnDropEx

Volá se rozhraním, když operace přetažení, která se má použít.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, které se ukazatel myši momentálně nachází.

*pDataObject*<br/>
Odkazuje na datový objekt, který obsahuje data, která mají být vyřazeny.

*dropDefault*<br/>
Efekt, který uživatel vybral pro operaci přetažení výchozí na základě aktuálního stavu klíče. Může být DROPEFFECT_NONE. Přetažení efekty jsou popsány v části poznámky.

*dropList*<br/>
Seznam rozevírací efekty, které podporuje zdroje přemístění. Přetažení efekt hodnoty lze spojovat pomocí bitový operátor OR (**&#124;**) operace. Přetažení efekty jsou popsány v části poznámky.

*point*<br/>
Obsahuje umístění kurzoru v pixelech, vzhledem k obrazovce.

### <a name="return-value"></a>Návratová hodnota

Přetažení efekt, který je výsledkem pokus odkládací umístění, které určuje *bodu*. Přetažení efekty jsou popsány v části poznámky.

### <a name="remarks"></a>Poznámky

Rozhraní volá nejprve tuto funkci. Pokud nezpracovává rozevírací nabídku, pak zavolá rozhraní [OnDrop](#ondrop). Obvykle se přepíše [ondropex –](../../mfc/reference/cview-class.md#ondropex) ve třídě zobrazení pro podporu stisknutí pravého tlačítka myši přetáhnout myší. Obvykle třída zobrazení [OnDrop](../../mfc/reference/cview-class.md#ondrop) se používá ke zpracování případu podpory pro jednoduché operace přetažení.

Výchozí implementace `COleDropTarget::OnDropEx` volání [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex). Ve výchozím nastavení [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex) jednoduše vrací fiktivní hodnoty k označení [OnDrop](#ondrop) by měla být volána členská funkce.

Přetažení účinky popisují akci přidruženou k operaci přetažení. Najdete v následujícím seznamu rozevírací účinky:

- Přetažení A DROPEFFECT_NONE nebude povolen.

- Operace kopírování A DROPEFFECT_COPY by byla prováděna.

- Operace přesunu A DROPEFFECT_MOVE by byla prováděna.

- Odkaz A DROPEFFECT_LINK z vyřazené dat na původní data by byla založena.

- DROPEFFECT_SCROLL znamená, že operace přetažení posuvníku se použije nebo dochází v cíli.

Další informace najdete v tématu [IDropTarget::Drop](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-drop) v sadě Windows SDK.

##  <a name="register"></a>  COleDropTarget::Register

Voláním této funkce zaregistrovat okna OLE knihovny DLL jako cíl přetažení. platné.

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okna, které se má zaregistrovat jako cíl přetažení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se registrace je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce musí být volána pro operace přetažení na přijetí.

Další informace najdete v tématu [RegisterDragDrop](/windows/desktop/api/ole2/nf-ole2-registerdragdrop) v sadě Windows SDK.

##  <a name="revoke"></a>  COleDropTarget::Revoke

Voláním této funkce před zničení jakékoli okno, který byl zaregistrován jako cíl přetažení přímo pomocí volání [zaregistrovat](#register) odebrat ze seznamu cílů přetažení.

```
virtual void Revoke();
```

### <a name="remarks"></a>Poznámky

Tato funkce je volána automaticky [OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy) obslužná rutina okna, která byla zaregistrována, takže obvykle není nutné explicitně voláním této funkce.

Další informace najdete v tématu [RevokeDragDrop](/windows/desktop/api/ole2/nf-ole2-revokedragdrop) v sadě Windows SDK.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC HIERSVR](../../visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC OCLIENT](../../visual-cpp-samples.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDropSource – třída](../../mfc/reference/coledropsource-class.md)
