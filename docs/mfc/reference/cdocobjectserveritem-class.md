---
title: Třída CDocObjectServerItem
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
ms.openlocfilehash: 1f0f5cf93aab35a17f7174b2beee0d1398564a3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375530"
---
# <a name="cdocobjectserveritem-class"></a>Třída CDocObjectServerItem

Implementuje slovesa serveru OLE speciálně pro servery DocObject.

## <a name="syntax"></a>Syntaxe

```
class CDocObjectServerItem : public COleServerItem
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|Vytvoří `CDocObjectServerItem` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDocObjectServerItem::GetDocument](#getdocument)|Načte ukazatel na dokument, který obsahuje položku.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDocObjectServerItem::Ondoverb](#ondoverb)|Volána k provedení slovesa.|
|[CDocObjectServerItem::OnHide](#onhide)|Vyvolá výjimku, pokud se rozhraní pokusí skrýt položku DocObject.|
|[CDocObjectServerItem::OnShow](#onshow)|Volat rámci, aby docObject položku na místě aktivní. Pokud položka není DocObject, volá [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow).|

## <a name="remarks"></a>Poznámky

`CDocObjectServerItem`definuje překážetelné členské funkce: [OnHide](#onhide), [OnDoVerb](#ondoverb)a [OnShow](#onshow).

Chcete-li použít `CDocObjectServerItem`, ujistěte se, že [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) přepsání ve vaší `COleServerDoc`odvozené třídy vrátí nový `CDocObjectServerItem` objekt. Pokud potřebujete změnit všechny funkce v položce, můžete vytvořit novou `CDocObjectServerItem`instanci vlastní odvozené třídy.

Další informace o docobjects naleznete v tématu [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) a [COleCmdUI](../../mfc/reference/colecmdui-class.md) v *odkaz knihovny MFC*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerPoložka](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdocob.h

## <a name="cdocobjectserveritemcdocobjectserveritem"></a><a name="cdocobjectserveritem"></a>CDocObjectServerItem::CDocObjectServerItem

Vytvoří `CDocObjectServerItem` objekt.

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*pServerDoc*<br/>
Ukazatel na dokument, který bude obsahovat novou položku DocObject.

*bAutoDelete*<br/>
Označuje, zda lze objekt odstranit při uvolnění odkazu na něj. Pokud je objekt nedílnou `CDocObjectServerItem` součástí dat dokumentu, nastavte argument na HODNOTU NEPRAVDA. Nastavte hodnotu TRUE, pokud je objekt sekundární strukturou používanou k identifikaci oblasti v datech dokumentu, kterou lze odstranit v rámci.

## <a name="cdocobjectserveritemgetdocument"></a><a name="getdocument"></a>CDocObjectServerItem::GetDocument

Načte ukazatel na dokument, který obsahuje položku.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dokument, který obsahuje položku; Null, pokud položka není součástí dokumentu.

### <a name="remarks"></a>Poznámky

To umožňuje přístup k dokumentu serveru, který jste předali jako argument konstruktoru [CDocObjectServerItem.](#cdocobjectserveritem)

## <a name="cdocobjectserveritemondoverb"></a><a name="ondoverb"></a>CDocObjectServerItem::Ondoverb

Volat rámci k provedení zadané sloveso.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iSponož*<br/>
Určuje sloveso, které má být spuštěno. Možné hodnoty naleznete v tématu [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá členskou funkci [OnShow,](#onshow) pokud je položka DocObject a je zadána OLEIVERB_INPLACEACTIVATE nebo OLEIVERB_SHOW. Pokud položka není DocObject nebo je zadánjiný sloveso, výchozí implementace volá [COleServerItem::OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb).

## <a name="cdocobjectserveritemonhide"></a><a name="onhide"></a>CDocObjectServerItem::OnHide

Volat rámci skrýt položku.

```
virtual void OnHide();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace vyvolá výjimku, pokud je položka DocObject. Aktivní položku DocObject nelze skrýt, protože přebírá celé zobrazení. Chcete-li, aby položka DocObject zmizela, musíte ji deaktivovat. Pokud položka není DocObject, výchozí implementace volá [COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide).

## <a name="cdocobjectserveritemonshow"></a><a name="onshow"></a>CDocObjectServerItem::OnShow

Volat rámci pokyn serverové aplikace, aby docObject položku na místě aktivní.

```
virtual void OnShow();
```

### <a name="remarks"></a>Poznámky

Pokud položka není DocObject, výchozí implementace volá [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen). Přepsat tuto funkci, pokud chcete provést speciální zpracování při otevírání položky DocObject.

## <a name="see-also"></a>Viz také

[COleServerItem – třída](../../mfc/reference/coleserveritem-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer – třída](../../mfc/reference/cdocobjectserver-class.md)<br/>
[COleDocObjectItem – třída](../../mfc/reference/coledocobjectitem-class.md)
