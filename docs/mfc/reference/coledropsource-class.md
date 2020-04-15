---
title: Třída COleDropSource
ms.date: 11/04/2016
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
helpviewer_keywords:
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
ms.openlocfilehash: 324c4b7273f021b43c319fb0a494ac843856c78a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375026"
---
# <a name="coledropsource-class"></a>Třída COleDropSource

Umožňuje přetažení dat na cíl přetažení.

## <a name="syntax"></a>Syntaxe

```
class COleDropSource : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleDropSource::COleDropSource](#coledropsource)|Vytvoří `COleDropSource` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleDropSource::GiveFeedback](#givefeedback)|Změní kurzor během operace přetažení myší.|
|[COleDropSource::OnBeginDrag](#onbegindrag)|Zpracovává zachycení myši během operace přetažení myší.|
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|Zkontroluje, zda má přetahování pokračovat.|

## <a name="remarks"></a>Poznámky

Třída [COleDropTarget](../../mfc/reference/coledroptarget-class.md) zpracovává přijímající část operace přetažení myší. Objekt `COleDropSource` je zodpovědný za určení, kdy začíná operace přetažení, poskytuje zpětnou vazbu během operace přetažení a určuje, kdy operace přetažení skončí.

Chcete-li `COleDropSource` použít objekt, stačí zavolat konstruktor. To zjednodušuje proces určení, jaké události, jako je například klepnutí myší, zahájit operaci přetažení pomocí [COleDataSource::DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)nebo [COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) funkce. Tyto funkce vytvoří `COleDropSource` objekt pro vás. Můžete chtít změnit výchozí chování `COleDropSource` overridable funkce. Tyto členské funkce budou volány ve vhodnou dobu v rámci.

Další informace o operacích přetažení pomocí technologie OLE naleznete v článku [OLE přetažení](../../mfc/drag-and-drop-ole.md).

Další informace naleznete v [tématu IDropSource](/windows/win32/api/oleidl/nn-oleidl-idropsource) v sadě Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="coledropsourcecoledropsource"></a><a name="coledropsource"></a>COleDropSource::COleDropSource

Vytvoří `COleDropSource` objekt.

```
COleDropSource();
```

## <a name="coledropsourcegivefeedback"></a><a name="givefeedback"></a>COleDropSource::GiveFeedback

Volat rámci po volání [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) nebo [COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>Parametry

*efekt přetažení*<br/>
Efekt, který chcete uživateli zobrazit, obvykle označující, co by se stalo, kdyby v tomto okamžiku došlo k poklesu s vybranými daty. Obvykle se jedná o hodnotu vrácenou posledním voláním [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) nebo [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover). Může to být jedna nebo více z následujících možností:

- DROPEFFECT_NONE Kapka by nebyla povolena.

- DROPEFFECT_COPY Bude provedena operace kopírování.

- DROPEFFECT_MOVE Bude provedena operace přesunutí.

- DROPEFFECT_LINK Bylo by vytvořeno propojení z vynechaná data s původními daty.

- DROPEFFECT_SCROLL Operace přetahování se chystá nebo dochází v cíli.

### <a name="return-value"></a>Návratová hodnota

Vrátí DRAGDROP_S_USEDEFAULTCURSORS pokud probíhá přetahování, noerror, pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci poskytnout zpětnou vazbu pro uživatele o tom, co by se stalo, kdyby došlo k poklesu v tomto okamžiku. Výchozí implementace používá výchozí kurzory OLE. Další informace o operacích přetažení pomocí technologie OLE naleznete v článku [OLE přetažení](../../mfc/drag-and-drop-ole.md).

Další informace naleznete v [tématech IDropSource::GiveFeedback](/windows/win32/api/oleidl/nf-oleidl-idropsource-givefeedback), [IDropTarget::DragOver](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover)a [IDropTarget::DragEnter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) v sadě Windows SDK.

## <a name="coledropsourceonbegindrag"></a><a name="onbegindrag"></a>COleDropSource::OnBeginDrag

Volat rámci při dojde k události, která by mohla zahájit operaci přetažení, jako je například stisknutí levého tlačítka myši.

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, které obsahuje vybraná data.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je přetažení povoleno, jinak 0.

### <a name="remarks"></a>Poznámky

Přepište tuto funkci, pokud chcete změnit způsob spuštění procesu přetahování. Výchozí implementace zachytí myš a zůstane v režimu přetažení, dokud uživatel neklepne na levé nebo pravé tlačítko myši nebo nedosáhne klávesy ESC, kdy uvolní myš.

## <a name="coledropsourcequerycontinuedrag"></a><a name="querycontinuedrag"></a>COleDropSource::QueryContinueDrag

Po zahájení přetahování je tato funkce opakovaně volána rámcem, dokud není operace přetažení zrušena nebo dokončena.

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>Parametry

*bEscapePressed*<br/>
zda byl klíč ESC stisknut od posledního volání . `COleDropSource::QueryContinueDrag`

*dwKeyState*<br/>
Obsahuje stav modifikačních kláves na klávesnici. Jedná se o kombinaci libovolného počtu: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

### <a name="return-value"></a>Návratová hodnota

DRAGDROP_S_CANCEL, pokud je stisknuto tlačítko ESC nebo pravé tlačítko nebo je před zahájením tažení zvednuto levé tlačítko. DRAGDROP_S_DROP, pokud by měla dojít k operaci přetažení. Jinak S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci, pokud chcete změnit bod, ve kterém je zrušeno přetažení nebo dojde k přetažení.

Výchozí implementace iniciuje přetažení nebo zruší přetažení následujícím způsobem. Zruší operaci přetažení po stisknutí klávesy ESC nebo pravého tlačítka myši. Zahájí operaci přetažení, když je po spuštění přetažení aktivováno levé tlačítko myši. V opačném případě vrátí S_OK a neprovede žádné další operace.

Vzhledem k tomu, že tato funkce se nazývá často, by měla být optimalizována co nejvíce.

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[OKLIENT ukázkový příklad knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
