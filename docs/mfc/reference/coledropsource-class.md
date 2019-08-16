---
title: COleDropSource – třída
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
ms.openlocfilehash: 3a1e27ca6c1019eb8716194b3b7711238d015d6d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504004"
---
# <a name="coledropsource-class"></a>COleDropSource – třída

Umožňuje přetáhnout data na cíl přetažení.

## <a name="syntax"></a>Syntaxe

```
class COleDropSource : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleDropSource::COleDropSource](#coledropsource)|`COleDropSource` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleDropSource::GiveFeedback](#givefeedback)|Změní kurzor během operace přetažení.|
|[COleDropSource::OnBeginDrag](#onbegindrag)|Zpracovává zachycení myši během operace přetažení myší.|
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|Zkontroluje, jestli chcete pokračovat v přetahování.|

## <a name="remarks"></a>Poznámky

Třída [COleDropTarget](../../mfc/reference/coledroptarget-class.md) zpracovává přijímající část operace přetažení. `COleDropSource` Objekt zodpovídá za určení, kdy začne operace přetažení, poskytne zpětnou vazbu během operace přetažení a určí, kdy operace přetažení skončí.

Chcete-li `COleDropSource` použít objekt, stačí volat konstruktor. Tím se zjednodušuje proces určení událostí, jako je kliknutí myší, zahájení operace přetažení pomocí [COleDataSource –::D odragdrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::D odragdrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)nebo [odvozenou třídu COleServerItem::D odragdrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) Function. Tyto funkce vytvoří `COleDropSource` objekt za vás. Možná budete chtít změnit výchozí chování `COleDropSource` přepisovatelných funkcí. Tyto členské funkce budou zavolány v příslušném okamžiku rozhraním.

Další informace o operacích přetažení pomocí technologie OLE naleznete v článku [přetahování myší (OLE)](../../mfc/drag-and-drop-ole.md).

Další informace najdete v tématu [IDropSource](/windows/win32/api/oleidl/nn-oleidl-idropsource) v Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXOLE. h

##  <a name="coledropsource"></a>COleDropSource::COleDropSource

`COleDropSource` Vytvoří objekt.

```
COleDropSource();
```

##  <a name="givefeedback"></a>COleDropSource:: GiveFeedback může zdroj

Volá se rozhraním po volání [COleDropTarget:: OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) nebo [COleDropTarget::D ragenter](../../mfc/reference/coledroptarget-class.md#ondragenter).

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>Parametry

*dropEffect*<br/>
Efekt, který by se měl zobrazit uživateli, který obvykle indikuje, co se stane, když v tuto chvíli došlo k přerušení s vybranými daty. Obvykle se jedná o hodnotu vrácenou posledním voláním metody [CView:: OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) nebo [CView:: OnDragOver](../../mfc/reference/cview-class.md#ondragover). Může to být jedna nebo víc z těchto možností:

- DROPEFFECT_NONE by se nepovolilo přetažení.

- DROPEFFECT_COPY by se prováděla operace kopírování.

- DROPEFFECT_MOVE by se provedla operace přesunutí.

- Bylo navázáno propojení z vynechaných dat na původní data DROPEFFECT_LINK.

- DROPEFFECT_SCROLL, že se v cíli vyskytuje nebo probíhá operace přetáhnutí.

### <a name="return-value"></a>Návratová hodnota

Vrátí DRAGDROP_S_USEDEFAULTCURSORS, pokud probíhá přetahování, a pokud není, dojde k chybě.

### <a name="remarks"></a>Poznámky

Potlačením této funkce poskytnete uživateli zpětnou vazbu o tom, co se stane, když v tomto okamžiku došlo k přerušení. Výchozí implementace používá výchozí kurzory OLE. Další informace o operacích přetažení pomocí technologie OLE naleznete v článku [přetahování myší (OLE)](../../mfc/drag-and-drop-ole.md).

Další informace naleznete v tématu [IDropSource:: GiveFeedback může zdroj](/windows/win32/api/oleidl/nf-oleidl-idropsource-givefeedback), [IDropTarget::D ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover)a [IDropTarget::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) v Windows SDK.

##  <a name="onbegindrag"></a>COleDropSource::OnBeginDrag

Volá se rozhraním, když dojde k události, která by mohla zahájit operaci přetažení, například stisknutím levého tlačítka myši.

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno obsahující vybraná data.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je povoleno přetahování, jinak 0.

### <a name="remarks"></a>Poznámky

Tuto funkci přepište, pokud chcete změnit způsob, jakým se spouští proces přetahování. Výchozí implementace zachytí myš a zůstane v režimu přetažení, dokud uživatel neklikne na levé nebo pravé tlačítko myši nebo dojde ke stisknutí klávesy ESC, kdy uvolní myš.

##  <a name="querycontinuedrag"></a>  COleDropSource::QueryContinueDrag

Po přetahování je tato funkce volána opakovaně rozhraním, dokud se operace přetažení buď neruší, nebo se nedokončí.

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>Parametry

*bEscapePressed*<br/>
Uvádí, zda byl od posledního volání metody `COleDropSource::QueryContinueDrag`stisknuta klávesa ESC.

*dwKeyState*<br/>
Obsahuje stav modifikačních kláves na klávesnici. Jedná se o kombinaci libovolného čísla z následujících možností: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

### <a name="return-value"></a>Návratová hodnota

DRAGDROP_S_CANCEL, pokud se stiskne klávesa ESC nebo pravé tlačítko, nebo se před spuštěním přetahování vyvolá tlačítko vlevo. DRAGDROP_S_DROP, pokud by došlo k operaci přetažení. Jinak S_OK.

### <a name="remarks"></a>Poznámky

Tuto funkci přepište, pokud chcete změnit bod, ve kterém se přetažení zruší nebo dojde k přerušení.

Výchozí implementace inicializuje přetažení nebo zruší následující přetahování. Po stisknutí klávesy ESC nebo pravého tlačítka myši zruší operaci přetažení. Inicializuje operaci přetažení, když se po zahájení tažení vyvolá levé tlačítko myši. V opačném případě vrátí hodnotu S_OK a neprovede žádné další operace.

Vzhledem k tomu, že se tato funkce nazývá často, měla by být optimalizovaná co nejvíce.

## <a name="see-also"></a>Viz také:

[HIERSVR Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[OCLIENT Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
