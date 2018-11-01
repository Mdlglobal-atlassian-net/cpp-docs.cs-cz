---
title: Coledropsource – třída
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
ms.openlocfilehash: 51d524054b67a5cecc5aa7791b0aeea0cc076813
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457778"
---
# <a name="coledropsource-class"></a>Coledropsource – třída

Umožňuje dat přetáhnout do cíle přetažení.

## <a name="syntax"></a>Syntaxe

```
class COleDropSource : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleDropSource::COleDropSource](#coledropsource)|Vytvoří `COleDropSource` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleDropSource::GiveFeedback](#givefeedback)|Změní kurzor během operace přetažení myší.|
|[COleDropSource::OnBeginDrag](#onbegindrag)|Zpracovává zachycení myši během operace přetažení myší.|
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|Kontroluje, zda tažení by měly pokračovat.|

## <a name="remarks"></a>Poznámky

[Coledroptarget –](../../mfc/reference/coledroptarget-class.md) třída zpracovává přijímající část operace přetažení myší. `COleDropSource` Objekt zodpovídá za určení, kdy začne operace přetažení, poskytování zpětné vazby během operace přetažení a určení po ukončení operace přetažení.

Použití `COleDropSource` objektu, stačí zavolat konstruktor. To zjednodušuje procesu, který určuje, jaké události, jako je například kliknutí myší, začněte pomocí operace přetažení [COleDataSource::DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop), nebo [ COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) funkce. Těchto funkcí vytvoří `COleDropSource` objekt za vás. Můžete chtít změnit výchozí chování `COleDropSource` přepisovatelné funkce. Tyto členské funkce bude volat rozhraní ve vhodných chvílích.

Další informace o operací přetažení myší pomocí OLE, najdete v článku [oblast pro přetažení přetažení (OLE)](../../mfc/drag-and-drop-ole.md).

Další informace najdete v tématu [IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource) v sadě Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

##  <a name="coledropsource"></a>  COleDropSource::COleDropSource

Vytvoří `COleDropSource` objektu.

```
COleDropSource();
```

##  <a name="givefeedback"></a>  COleDropSource::GiveFeedback

Volá se rozhraním po volání [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) nebo [COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>Parametry

*dropEffect*<br/>
Účinek, který se má zobrazit uživateli, obvykle označující, co by mohlo dojít, pokud přetažení došlo k chybě v tuto chvíli se vybraná data. Obvykle je to hodnota vrácená voláním nejnovější [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) nebo [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover). Může být jeden nebo více z následujících akcí:

- Přetažení A DROPEFFECT_NONE nebude povolen.

- Operace kopírování A DROPEFFECT_COPY by byla prováděna.

- Operace přesunu A DROPEFFECT_MOVE by byla prováděna.

- Odkaz A DROPEFFECT_LINK z vyřazené dat na původní data by byla založena.

- DROPEFFECT_SCROLL A přetažením posuvníku operace se použije nebo dochází v cíli.

### <a name="return-value"></a>Návratová hodnota

Vrátí DRAGDROP_S_USEDEFAULTCURSORS Pokud přetažením právě probíhá, NOERROR, pokud není.

### <a name="remarks"></a>Poznámky

Potlačí tuto funkci pro poskytnutí zpětné vazby uživatelů o co by mohlo dojít, pokud přetažení došlo k chybě v tomto okamžiku. Výchozí implementace používá výchozí kurzory OLE. Další informace o operací přetažení myší pomocí OLE, najdete v článku [oblast pro přetažení přetažení (OLE)](../../mfc/drag-and-drop-ole.md).

Další informace najdete v tématu [IDropSource::GiveFeedback](/windows/desktop/api/oleidl/nf-oleidl-idropsource-givefeedback), [IDropTarget::DragOver](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragover), a [IDropTarget::DragEnter](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragenter) v sadě Windows SDK.

##  <a name="onbegindrag"></a>  COleDropSource::OnBeginDrag

Volá framework při výskytu události, která by mohla spustit operaci přetažení, jako je například stisknutí levého tlačítka myši.

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, obsahující vybrané údaje.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud přetažení je povoleno, jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce přepište, pokud chcete změnit způsob, jakým je spuštěn proces přetahování. Výchozí implementace zachytí myš a zůstane v režimu přetažení, dokud uživatel stiskne tlačítko myši doleva nebo doprava nebo volání ESC, po kterém ho uvolní tlačítko myši.

##  <a name="querycontinuedrag"></a>  COleDropSource::QueryContinueDrag

Po přetažení, tato funkce je volána opakovaně rozhraním, dokud nebude operace přetažení zrušena nebo dokončení.

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>Parametry

*bEscapePressed*<br/>
Uvádí, zda byla od posledního volání stisknuta klávesa ESC `COleDropSource::QueryContinueDrag`.

*dwKeyState*<br/>
Obsahuje informace o stavu modifikační klávesy na klávesnici. Jedná se o kombinaci libovolný počet následující: MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

### <a name="return-value"></a>Návratová hodnota

DRAGDROP_S_CANCEL Pokud klávesy ESC nebo pravým tlačítkem je stisknutí nebo levého tlačítka je aktivována před přetažením spustí. DRAGDROP_S_DROP, pokud dojde k operaci přetažení. Jinak S_OK.

### <a name="remarks"></a>Poznámky

Dojde k přepsání, které tuto funkci Pokud chcete změnit bod, ve které přetažení se zruší nebo přetažení.

Výchozí implementace zahájí rozevíracího nebo zruší přetahování následujícím způsobem. Operace přetažení zruší po stisknutí klávesy ESC nebo pravým tlačítkem myši. Při vyvolání levé tlačítko myši po přetažení spuštění zahájení operace přetažení. V opačném případě vrátí hodnotu S_OK a provádí žádné další operace.

Protože tato funkce je volána často, to by mělo být optimalizované co největší míře.

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC HIERSVR](../../visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC OCLIENT](../../visual-cpp-samples.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

