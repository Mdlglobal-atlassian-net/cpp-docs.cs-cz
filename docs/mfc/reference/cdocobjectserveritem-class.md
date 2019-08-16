---
title: CDocObjectServerItem Class
ms.date: 03/27/2019
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnDoVerb
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnDoVerb
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
ms.openlocfilehash: 4d44791415626f1a94500b9c3885581d67e8fe42
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506822"
---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServerItem Class

Implementuje příkazy OLE serveru konkrétně pro DocObject servery.

## <a name="syntax"></a>Syntaxe

```
class CDocObjectServerItem : public COleServerItem
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name|Popis|
|----------|-----------------|
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|`CDocObjectServerItem` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CDocObjectServerItem::GetDocument](#getdocument)|Načte ukazatel na dokument, který obsahuje položku.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CDocObjectServerItem::OnDoVerb](#ondoverb)|Volá se, aby se spustil příkaz.|
|[CDocObjectServerItem::OnHide](#onhide)|Vyvolá výjimku, pokud se systém pokusí skrýt položku DocObject.|
|[CDocObjectServerItem::OnShow](#onshow)|Volá se rozhraním, aby se provedla místní aktivace položky DocObject. Pokud položka není DocObject, volá [odvozenou třídu COleServerItem:: inshow](../../mfc/reference/coleserveritem-class.md#onshow).|

## <a name="remarks"></a>Poznámky

`CDocObjectServerItem`definuje přepsatelné členské funkce: [Hide](#onhide), [OnDoVerb](#ondoverb)a inshow [](#onshow).

Chcete- `CDocObjectServerItem`li použít, zajistěte, aby `COleServerDoc`přepsání [funkci OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) v odvozené třídě vrátilo nový `CDocObjectServerItem` objekt. Pokud potřebujete změnit všechny funkce v položce, můžete vytvořit novou instanci vlastní `CDocObjectServerItem`odvozené třídy.

Další informace o DocObjects naleznete v tématu [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) a [COleCmdUI](../../mfc/reference/colecmdui-class.md) v *Referenci knihovny MFC*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AfxDocOb. h

##  <a name="cdocobjectserveritem"></a>  CDocObjectServerItem::CDocObjectServerItem

`CDocObjectServerItem` Vytvoří objekt.

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*pServerDoc*<br/>
Ukazatel na dokument, který bude obsahovat novou položku DocObject.

*bAutoDelete*<br/>
Určuje, zda lze objekt odstranit, pokud je uvolněn odkaz na něj. Nastavte argument na hodnotu false, pokud `CDocObjectServerItem` je objekt nedílnou součástí dat dokumentu. Nastavte na hodnotu TRUE, pokud je objekt sekundární strukturou použitou k identifikaci rozsahu v datech v dokumentu, který může rozhraní odstranit.

##  <a name="getdocument"></a>CDocObjectServerItem:: GetDocument

Načte ukazatel na dokument, který obsahuje položku.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dokument, který obsahuje položku; Hodnota NULL, pokud položka není součástí dokumentu.

### <a name="remarks"></a>Poznámky

To umožňuje přístup k dokumentu serveru, který jste předali jako argument konstruktoru [CDocObjectServerItem](#cdocobjectserveritem) .

##  <a name="ondoverb"></a>  CDocObjectServerItem::OnDoVerb

Volá se rozhraním, aby se dala provést Zadaná operace.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Určuje operaci, která má být provedena. Možné hodnoty naleznete v tématu [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) v Windows SDK.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá členskou funkci [Inshow](#onshow) , pokud je položka DocObject a je ZADÁN parametr OLEIVERB_INPLACEACTIVATE nebo OLEIVERB_SHOW. Pokud položka není DocObject nebo je zadán jiný příkaz, výchozí implementace volá [odvozenou třídu COleServerItem:: OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb).

##  <a name="onhide"></a>CDocObjectServerItem:: Hide

Volá se rozhraním, aby se skryla položka.

```
virtual void OnHide();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace vyvolá výjimku, pokud je položka DocObject. Nemůžete skrýt aktivní položku DocObject, protože to trvá celé zobrazení. Je nutné deaktivovat položku DocObject, aby zmizela. Pokud položka není DocObject, výchozí implementace volá [odvozenou třídu COleServerItem:: Hide](../../mfc/reference/coleserveritem-class.md#onhide).

##  <a name="onshow"></a>CDocObjectServerItem:: inshow

Volá se rozhraním, aby se serverová aplikace pověřila, aby byla aktivní místní DocObject položka.

```
virtual void OnShow();
```

### <a name="remarks"></a>Poznámky

Pokud položka není DocObject, výchozí implementace volá [odvozenou třídu COleServerItem:: inshow](../../mfc/reference/coleserveritem-class.md#onopen). Tuto funkci můžete přepsat, pokud chcete při otevírání položky DocObject provádět zvláštní zpracování.

## <a name="see-also"></a>Viz také:

[COleServerItem – třída](../../mfc/reference/coleserveritem-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer – třída](../../mfc/reference/cdocobjectserver-class.md)<br/>
[COleDocObjectItem – třída](../../mfc/reference/coledocobjectitem-class.md)
