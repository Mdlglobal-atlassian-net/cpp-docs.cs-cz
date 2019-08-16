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
ms.openlocfilehash: 891b19112c8baf2efb088f064892e1ea19a7deab
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503967"
---
# <a name="coledroptarget-class"></a>COleDropTarget – třída

Poskytuje komunikační mechanismus mezi oknem a knihovnami OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDropTarget : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleDropTarget::COleDropTarget](#coledroptarget)|`COleDropTarget` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleDropTarget::OnDragEnter](#ondragenter)|Volá se, když ukazatel poprvé vstoupí do okna.|
|[COleDropTarget::OnDragLeave](#ondragleave)|Volá se, když se ukazatel myši přetáhne mimo okno.|
|[COleDropTarget::OnDragOver](#ondragover)|Volá se opakovaně, když se ukazatel myši přetáhne přes okno.|
|[COleDropTarget::OnDragScroll](#ondragscroll)|Volá se, aby se určilo, jestli se kurzor přetáhne do oblasti posouvání okna.|
|[COleDropTarget::OnDrop](#ondrop)|Volá se, když se data přeruší do okna, což je výchozí obslužná rutina.|
|[COleDropTarget::OnDropEx](#ondropex)|Volá se, když se data přeruší do okna, počáteční obslužné rutiny.|
|[COleDropTarget::Register](#register)|Zaregistruje okno jako platný cíl přetažení.|
|[COleDropTarget:: REVOKE](#revoke)|Způsobí, že okno přestane přerušit platný cíl přetažení.|

## <a name="remarks"></a>Poznámky

Vytvoření objektu této třídy umožňuje oknu přijímat data prostřednictvím mechanismu přetažení OLE.

Chcete-li získat okno pro přijetí příkazů drop, měli byste nejprve vytvořit objekt `COleDropTarget` třídy a pak zavolat funkci [Register](#register) s ukazatelem na požadovaný `CWnd` objekt jako jediný parametr.

Další informace o operacích přetažení pomocí technologie OLE naleznete v článku [přetahování myší (OLE)](../../mfc/drag-and-drop-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXOLE. h

##  <a name="coledroptarget"></a>COleDropTarget::COleDropTarget

Vytvoří objekt třídy `COleDropTarget`.

```
COleDropTarget();
```

### <a name="remarks"></a>Poznámky

Zavoláním metody [Register](#register) přidružíte tento objekt k oknu.

##  <a name="ondragenter"></a>COleDropTarget::OnDragEnter

Volá se rozhraním, když se ukazatel poprvé přetáhne do okna.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, na které se kurzor zadává.

*pDataObject*<br/>
Odkazuje na datový objekt obsahující data, která je možné vyřadit.

*dwKeyState*<br/>
Obsahuje stav modifikačních kláves. Jedná se o kombinaci libovolného čísla z následujících možností: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*Vyberte*<br/>
Obsahuje aktuální umístění kurzoru v souřadnicích klienta.

### <a name="return-value"></a>Návratová hodnota

Efekt, který by způsobil, pokud došlo k pokusu o zrušení v umístění určeném *bodem*. Může to být jedna nebo víc z těchto možností:

- DROPEFFECT_NONE by se nepovolilo přetažení.

- DROPEFFECT_COPY by se prováděla operace kopírování.

- DROPEFFECT_MOVE by se provedla operace přesunutí.

- Bylo navázáno propojení z vynechaných dat na původní data DROPEFFECT_LINK.

- DROPEFFECT_SCROLL, že se v cíli vyskytuje nebo probíhá operace přetáhnutí.

### <a name="remarks"></a>Poznámky

Tuto funkci přepište, pokud chcete, aby se v okně mohly vyskytovat operace drop. Výchozí implementace volá příkaz [CView:: OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), který ve výchozím nastavení jednoduše vrátí DROPEFFECT_NONE.

Další informace najdete v tématu [IDropTarget::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) v Windows SDK.

##  <a name="ondragleave"></a>  COleDropTarget::OnDragLeave

Volá se rozhraním, když kurzor opustí okno, zatímco je aktivní operace přetažení.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, které opouští kurzor.

### <a name="remarks"></a>Poznámky

Tuto funkci můžete přepsat, pokud chcete speciální chování, když operace přetažení opustí určené okno. Výchozí implementace této funkce volá metodu [CView:: OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).

Další informace najdete v tématu [IDropTarget::D ragleave](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave) v Windows SDK.

##  <a name="ondragover"></a>COleDropTarget::OnDragOver

Volá se rozhraním, když se ukazatel myši přetáhne přes okno.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, ve kterém se nachází kurzor.

*pDataObject*<br/>
Odkazuje na datový objekt obsahující data, která mají být vyhozena.

*dwKeyState*<br/>
Obsahuje stav modifikačních kláves. Jedná se o kombinaci libovolného čísla z následujících možností: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*Vyberte*<br/>
Obsahuje aktuální umístění kurzoru v souřadnicích klienta.

### <a name="return-value"></a>Návratová hodnota

Efekt, který by způsobil, pokud došlo k pokusu o zrušení v umístění určeném *bodem*. Může to být jedna nebo víc z těchto možností:

- DROPEFFECT_NONE by se nepovolilo přetažení.

- DROPEFFECT_COPY by se prováděla operace kopírování.

- DROPEFFECT_MOVE by se provedla operace přesunutí.

- Bylo navázáno propojení z vynechaných dat na původní data DROPEFFECT_LINK.

- DROPEFFECT_SCROLL označuje, že v cíli dojde k operaci přetažení, která se chystá nebo k ní dochází.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být přepsána, aby se v okně mohly objevit operace drop. Výchozí implementace této funkce volá příkaz [CView:: OnDragOver](../../mfc/reference/cview-class.md#ondragover), který ve výchozím nastavení vrátí DROPEFFECT_NONE. Vzhledem k tomu, že je tato funkce volána často během operace přetažení, měla by být optimalizována co nejvíce.

Další informace najdete v tématu [IDropTarget::D ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

##  <a name="ondragscroll"></a>  COleDropTarget::OnDragScroll

Volá se rozhraním, než se zavolá [OnDragEnter](#ondragenter) nebo [OnDragOver](#ondragover) , aby se zjistilo, jestli je *bod* v oblasti posouvání.

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazuje na okno, na kterém je kurzor právě nainstalovaná.

*dwKeyState*<br/>
Obsahuje stav modifikačních kláves. Jedná se o kombinaci libovolného čísla z následujících možností: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*Vyberte*<br/>
Obsahuje umístění kurzoru v pixelech vzhledem k obrazovce.

### <a name="return-value"></a>Návratová hodnota

Efekt, který by způsobil, pokud došlo k pokusu o zrušení v umístění určeném *bodem*. Může to být jedna nebo víc z těchto možností:

- DROPEFFECT_NONE by se nepovolilo přetažení.

- DROPEFFECT_COPY by se prováděla operace kopírování.

- DROPEFFECT_MOVE by se provedla operace přesunutí.

- Bylo navázáno propojení z vynechaných dat na původní data DROPEFFECT_LINK.

- DROPEFFECT_SCROLL označuje, že v cíli dojde k operaci přetažení, která se chystá nebo k ní dochází.

### <a name="remarks"></a>Poznámky

Tuto funkci popište, pokud chcete pro tuto událost zadat zvláštní chování. Výchozí implementace této funkce volá příkaz [CView:: OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), který vrátí DROPEFFECT_NONE, a posune okno, když je kurzor přetažen do výchozí oblasti posunu uvnitř ohraničení okna.

##  <a name="ondrop"></a>COleDropTarget:: drop – přetažení

Volá se rozhraním, když dojde k operaci přetažení.

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazuje na okno, na kterém je kurzor právě nainstalovaná.

*pDataObject*<br/>
Odkazuje na datový objekt obsahující data, která mají být vyhozena.

*dropEffect*<br/>
Efekt, který uživatel zvolil pro operaci drop. Může to být jedna nebo víc z těchto možností:

- DROPEFFECT_COPY by se prováděla operace kopírování.

- DROPEFFECT_MOVE by se provedla operace přesunutí.

- Bylo navázáno propojení z vynechaných dat na původní data DROPEFFECT_LINK.

*Vyberte*<br/>
Obsahuje umístění kurzoru v pixelech vzhledem k obrazovce.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je přetažení úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Rozhraní nejprve zavolá [OnDropEx](#ondropex). Pokud funkce nezpracovává přetažení, rozhraní volá tuto členskou funkci, `OnDrop`. `OnDropEx` Obvykle aplikace Přepisuje [OnDropEx](../../mfc/reference/cview-class.md#ondropex) ve třídě zobrazení a zpracovává tak pravé tlačítko myši a přetahování myší. Obvykle se pro zpracování jednoduchého přetahování používá třída zobrazení [drop](../../mfc/reference/cview-class.md#ondrop) .

Výchozí implementace `COleDropTarget::OnDrop` volání [CView:: drop](../../mfc/reference/cview-class.md#ondrop), která jednoduše vrátí hodnotu false ve výchozím nastavení.

Další informace najdete v tématu [IDropTarget::D pravém](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) v Windows SDK.

##  <a name="ondropex"></a>COleDropTarget::OnDropEx

Volá se rozhraním, když dojde k operaci přetažení.

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
Ukazuje na okno, na kterém je kurzor právě nainstalovaná.

*pDataObject*<br/>
Odkazuje na datový objekt obsahující data, která mají být vyhozena.

*dropDefault*<br/>
Efekt, který uživatel zvolil pro výchozí operaci přetažení založenou na aktuálním stavu klíče. Může to být DROPEFFECT_NONE. Efekty přetažení jsou popsány v části poznámky.

*dropList*<br/>
Seznam efektů přetažení, které podporuje zdroj přetažení. Hodnoty efektu přetažení lze kombinovat pomocí operace bitového **&#124;** operátoru OR (). Efekty přetažení jsou popsány v části poznámky.

*Vyberte*<br/>
Obsahuje umístění kurzoru v pixelech vzhledem k obrazovce.

### <a name="return-value"></a>Návratová hodnota

Efekt odtažení, který vyplynule z pokusu o zrušení v umístění určeném *bodem*. Efekty přetažení jsou popsány v části poznámky.

### <a name="remarks"></a>Poznámky

Rozhraní nejprve volá tuto funkci. Pokud nezpracovává přetažení, pak rozhraní volá metodu [drop](#ondrop). Obvykle přepíšete [OnDropEx](../../mfc/reference/cview-class.md#ondropex) ve třídě zobrazení tak, aby podporovala pravé tlačítko myši a přetažení myší. Obvykle se při vyřazení [](../../mfc/reference/cview-class.md#ondrop) třídy zobrazení používá ke zpracování případu podpory jednoduchého přetahování.

Výchozí implementace `COleDropTarget::OnDropEx` volání [CView:: OnDropEx](../../mfc/reference/cview-class.md#ondropex). Ve výchozím nastavení funkce [CView:: OnDropEx](../../mfc/reference/cview-class.md#ondropex) jednoduše vrátí fiktivní hodnotu, aby označovala, že by měla být volána členská funkce [drop](#ondrop) .

Efekty přetažení popisují akci přidruženou k operaci drop. Podívejte se na následující seznam efektů přetažení:

- DROPEFFECT_NONE by se nepovolilo přetažení.

- DROPEFFECT_COPY by se prováděla operace kopírování.

- DROPEFFECT_MOVE by se provedla operace přesunutí.

- Bylo navázáno propojení z vynechaných dat na původní data DROPEFFECT_LINK.

- DROPEFFECT_SCROLL označuje, že v cíli dojde k operaci přetažení, která se chystá nebo k ní dochází.

Další informace najdete v tématu [IDropTarget::D pravém](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) v Windows SDK.

##  <a name="register"></a>COleDropTarget:: Register

Voláním této funkce zaregistrujete okno s knihovnami DLL OLE jako platný cíl přetažení.

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, které má být registrováno jako cíl přetažení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je registrace úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Aby bylo možné operace odkládacího umístění přijmout, musí být tato funkce volána.

Další informace najdete v tématu [RegisterDragDrop](/windows/win32/api/ole2/nf-ole2-registerdragdrop) v Windows SDK.

##  <a name="revoke"></a>COleDropTarget:: REVOKE

Tuto funkci volejte před zničením okna, které bylo registrováno jako cíl přetažení prostřednictvím volání k [registraci](#register) pro odebrání ze seznamu cílů přetažení.

```
virtual void Revoke();
```

### <a name="remarks"></a>Poznámky

Tato funkce je volána automaticky z obslužné rutiny [zničení](../../mfc/reference/cwnd-class.md#ondestroy) pro okno, které bylo zaregistrováno, takže obvykle není nutné volat tuto funkci explicitně.

Další informace najdete v tématu [RevokeDragDrop](/windows/win32/api/ole2/nf-ole2-revokedragdrop) v Windows SDK.

## <a name="see-also"></a>Viz také:

[HIERSVR Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[OCLIENT Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDropSource – třída](../../mfc/reference/coledropsource-class.md)
