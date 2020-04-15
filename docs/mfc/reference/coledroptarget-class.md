---
title: COleDropTarget – třída
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
ms.openlocfilehash: 01eb277da029d06ee44d8e048cf3244f4371a9ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374997"
---
# <a name="coledroptarget-class"></a>COleDropTarget – třída

Poskytuje mechanismus komunikace mezi oknem a knihovnami OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDropTarget : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleDropTarget::COleDropTarget](#coledroptarget)|Vytvoří `COleDropTarget` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[ColeDropTarget::OnDragEnter](#ondragenter)|Volána při prvním vstupu kurzoru do okna.|
|[ColeDropTarget::OnDragleave](#ondragleave)|Volána při přetažení kurzoru z okna.|
|[ColeDropTarget::OnDragover](#ondragover)|Voláno opakovaně při přetažení kurzoru přes okno.|
|[ColeDropTarget::ondragscroll](#ondragscroll)|Volána k určení, zda je kurzor přetažen do oblasti posouvání okna.|
|[ColeDropTarget::Ondrop](#ondrop)|Volána při přehození dat do okna, výchozí obslužná rutina.|
|[ColeDropTarget::OnDropEx](#ondropex)|Volána při přehození dat do okna, počáteční obslužná rutina.|
|[COleDropTarget::Registrovat](#register)|Zaregistruje okno jako platný cíl přetažení.|
|[COleDropTarget::Odvolat](#revoke)|Způsobí, že okno přestane být platný cíl přetažení.|

## <a name="remarks"></a>Poznámky

Vytvoření objektu této třídy umožňuje okno přijímat data prostřednictvím mechanismu ole přetažení.

Chcete-li získat okno pro přijetí příkazů přetažení, `COleDropTarget` měli byste nejprve vytvořit objekt třídy `CWnd` a potom volat [Register](#register) funkce s ukazatelem na požadovaný objekt jako jediný parametr.

Další informace o operacích přetažení pomocí technologie OLE naleznete v článku [OLE přetažení](../../mfc/drag-and-drop-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="coledroptargetcoledroptarget"></a><a name="coledroptarget"></a>COleDropTarget::COleDropTarget

Vytvoří objekt třídy `COleDropTarget`.

```
COleDropTarget();
```

### <a name="remarks"></a>Poznámky

Volání [Register](#register) přidružit tento objekt k oknu.

## <a name="coledroptargetondragenter"></a><a name="ondragenter"></a>ColeDropTarget::OnDragEnter

Volat rámci při prvním přetažení kurzoru do okna.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazuje na okno, do které kurzor vstupuje.

*objekt pDataObject*<br/>
Odkazuje na datový objekt obsahující data, která mohou být vynechána.

*dwKeyState*<br/>
Obsahuje stav modifikačních klíčů. Jedná se o kombinaci libovolného počtu: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*Bod*<br/>
Obsahuje aktuální umístění kurzoru v souřadnicích klienta.

### <a name="return-value"></a>Návratová hodnota

Efekt, který by měl za následek, pokud by došlo k pokusu o pokles v umístění určeném *bodem*. Může to být jedna nebo více z následujících možností:

- DROPEFFECT_NONE Kapka by nebyla povolena.

- DROPEFFECT_COPY Bude provedena operace kopírování.

- DROPEFFECT_MOVE Bude provedena operace přesunutí.

- DROPEFFECT_LINK Bylo by vytvořeno propojení z vynechaná data s původními daty.

- DROPEFFECT_SCROLL Operace přetahování se chystá nebo dochází v cíli.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci povolit přetažení operace dojít v okně. Výchozí implementace volá [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), který jednoduše vrátí DROPEFFECT_NONE ve výchozím nastavení.

Další informace naleznete v tématu [IDropTarget::DragEnter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) v sadě Windows SDK.

## <a name="coledroptargetondragleave"></a><a name="ondragleave"></a>ColeDropTarget::OnDragleave

Volat rámci při kurzor opustí okno, zatímco operace přetažení je v platnosti.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazuje na okno, které kurzor opouští.

### <a name="remarks"></a>Poznámky

Tuto funkci přepište, pokud chcete zvláštní chování, když operace přetažení opustí zadané okno. Výchozí implementace této funkce volá [CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).

Další informace naleznete v tématu [IDropTarget::DragLeave](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave) v sadě Windows SDK.

## <a name="coledroptargetondragover"></a><a name="ondragover"></a>ColeDropTarget::OnDragover

Volat rámci při přetažení kurzoru přes okno.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, nad kterým je kurzor.

*objekt pDataObject*<br/>
Odkazuje na datový objekt, který obsahuje data, která mají být vynechána.

*dwKeyState*<br/>
Obsahuje stav modifikačních klíčů. Jedná se o kombinaci libovolného počtu: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*Bod*<br/>
Obsahuje aktuální umístění kurzoru v souřadnicích klienta.

### <a name="return-value"></a>Návratová hodnota

Efekt, který by měl za následek, pokud by došlo k pokusu o pokles v umístění určeném *bodem*. Může to být jedna nebo více z následujících možností:

- DROPEFFECT_NONE Kapka by nebyla povolena.

- DROPEFFECT_COPY Bude provedena operace kopírování.

- DROPEFFECT_MOVE Bude provedena operace přesunutí.

- DROPEFFECT_LINK Bylo by vytvořeno propojení z vynechaná data s původními daty.

- DROPEFFECT_SCROLL Označuje, že operace přetahování se chystá dojít nebo dochází v cíli.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být přepsána, aby operace přetažení v okně. Výchozí implementace této funkce volá [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover), který vrací DROPEFFECT_NONE ve výchozím nastavení. Vzhledem k tomu, že tato funkce je volána často během operace přetažení myší, měla by být co nejvíce optimalizována.

Další informace naleznete v tématu [IDropTarget::DragOver](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

## <a name="coledroptargetondragscroll"></a><a name="ondragscroll"></a>ColeDropTarget::ondragscroll

Volat rámci před voláním [OnDragEnter](#ondragenter) nebo [OnDragOver](#ondragover) k *určení,* zda bod je v oblasti posouvání.

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, nad které je kurzor právě u konce.

*dwKeyState*<br/>
Obsahuje stav modifikačních klíčů. Jedná se o kombinaci libovolného počtu: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*Bod*<br/>
Obsahuje umístění kurzoru v obrazových bodech vzhledem k obrazovce.

### <a name="return-value"></a>Návratová hodnota

Efekt, který by měl za následek, pokud by došlo k pokusu o pokles v umístění určeném *bodem*. Může to být jedna nebo více z následujících možností:

- DROPEFFECT_NONE Kapka by nebyla povolena.

- DROPEFFECT_COPY Bude provedena operace kopírování.

- DROPEFFECT_MOVE Bude provedena operace přesunutí.

- DROPEFFECT_LINK Bylo by vytvořeno propojení z vynechaná data s původními daty.

- DROPEFFECT_SCROLL Označuje, že operace přetahování se chystá dojít nebo dochází v cíli.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci, pokud chcete poskytnout speciální chování pro tuto událost. Výchozí implementace této funkce volá [CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), který vrátí DROPEFFECT_NONE a posune okno při přetažení kurzoru do výchozí oblasti posouvání uvnitř okraje okna.

## <a name="coledroptargetondrop"></a><a name="ondrop"></a>ColeDropTarget::Ondrop

Volat rámci při přetažení operace dojde.

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, nad které je kurzor právě u konce.

*objekt pDataObject*<br/>
Odkazuje na datový objekt, který obsahuje data, která mají být vynechána.

*efekt přetažení*<br/>
Efekt, který uživatel zvolil pro operaci přetažení. Může to být jedna nebo více z následujících možností:

- DROPEFFECT_COPY Bude provedena operace kopírování.

- DROPEFFECT_MOVE Bude provedena operace přesunutí.

- DROPEFFECT_LINK Bylo by vytvořeno propojení z vynechaná data s původními daty.

*Bod*<br/>
Obsahuje umístění kurzoru v obrazových bodech vzhledem k obrazovce.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je pokles úspěšný; jinak 0.

### <a name="remarks"></a>Poznámky

Rozhraní Framework nejprve volá [OnDropEx](#ondropex). Pokud `OnDropEx` funkce nezpracovává přetažení, framework pak volá `OnDrop`tuto člennou funkci . Aplikace obvykle přepíše [OnDropEx](../../mfc/reference/cview-class.md#ondropex) v view třídy pro zpracování pravé tlačítko myši přetáhnout. Třída zobrazení [OnDrop](../../mfc/reference/cview-class.md#ondrop) se obvykle používá ke zpracování jednoduchého přetažení.

Výchozí implementace `COleDropTarget::OnDrop` volání [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop), který jednoduše vrátí false ve výchozím nastavení.

Další informace naleznete v tématu [IDropTarget::Drop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) v sadě Windows SDK.

## <a name="coledroptargetondropex"></a><a name="ondropex"></a>ColeDropTarget::OnDropEx

Volat rámci při přetažení operace dojde.

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
Odkazuje na okno, nad které je kurzor právě u konce.

*objekt pDataObject*<br/>
Odkazuje na datový objekt, který obsahuje data, která mají být vynechána.

*přetaženíVýchozí*<br/>
Efekt, který uživatel zvolil pro výchozí operaci přetažení na základě aktuálního stavu klíče. Dá se to DROPEFFECT_NONE. Efekty přetažení jsou popsány v části Poznámky.

*dropList*<br/>
Seznam efektů přetažení, které podporuje zdroj přetažení. Hodnoty efektu přetažení lze kombinovat pomocí bitové operace OR (**&#124;). ** Efekty přetažení jsou popsány v části Poznámky.

*Bod*<br/>
Obsahuje umístění kurzoru v obrazových bodech vzhledem k obrazovce.

### <a name="return-value"></a>Návratová hodnota

Efekt přetažení, který byl výsledkem pokusu o přetažení v umístění určeném *bodem*. Efekty přetažení jsou popsány v části Poznámky.

### <a name="remarks"></a>Poznámky

Rozhraní framework nejprve volá tuto funkci. Pokud nezpracovává přetažení, pak framework volá [OnDrop](#ondrop). Obvykle přepíšete [OnDropEx](../../mfc/reference/cview-class.md#ondropex) ve třídě zobrazení pro podporu pravého tlačítka myši přetažení. Třídu zobrazení [OnDrop](../../mfc/reference/cview-class.md#ondrop) se obvykle používá ke zpracování případu podpory pro jednoduché přetažení.

Výchozí implementace `COleDropTarget::OnDropEx` volání [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex). Ve výchozím nastavení [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex) jednoduše vrátí fiktivní hodnotu označující, že by měla být volána členská funkce [OnDrop.](#ondrop)

Efekty přetažení popisují akci přidruženou k operaci přetažení. Podívejte se na následující seznam efektů přetažení:

- DROPEFFECT_NONE Kapka by nebyla povolena.

- DROPEFFECT_COPY Bude provedena operace kopírování.

- DROPEFFECT_MOVE Bude provedena operace přesunutí.

- DROPEFFECT_LINK Bylo by vytvořeno propojení z vynechaná data s původními daty.

- DROPEFFECT_SCROLL Označuje, že operace přetahování se chystá dojít nebo dochází v cíli.

Další informace naleznete v tématu [IDropTarget::Drop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) v sadě Windows SDK.

## <a name="coledroptargetregister"></a><a name="register"></a>COleDropTarget::Registrovat

Volání této funkce zaregistrovat okno s OLE Knihovny DLL jako platný cíl přetažení.

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, které má být registrováno jako cíl přetažení.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je registrace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce musí být volána pro operace přetažení, které mají být přijaty.

Další informace naleznete v tématu [RegisterDragDrop](/windows/win32/api/ole2/nf-ole2-registerdragdrop) v sadě Windows SDK.

## <a name="coledroptargetrevoke"></a><a name="revoke"></a>COleDropTarget::Odvolat

Volání této funkce před zničením libovolné okno, které bylo registrováno jako cíl přetažení prostřednictvím volání [Register](#register) odebrat ze seznamu cílů přetažení.

```
virtual void Revoke();
```

### <a name="remarks"></a>Poznámky

Tato funkce je volána automaticky z [OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy) obslužné rutiny pro okno, které bylo registrováno, takže obvykle není nutné volat tuto funkci explicitně.

Další informace naleznete v tématu [RevokeDragDrop](/windows/win32/api/ole2/nf-ole2-revokedragdrop) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[OKLIENT ukázkový příklad knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída COleDropSource](../../mfc/reference/coledropsource-class.md)
