---
title: CRichEditCntrItem – třída
ms.date: 11/04/2016
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
helpviewer_keywords:
- CRichEditCntrItem [MFC], CRichEditCntrItem
- CRichEditCntrItem [MFC], SyncToRichEditObject
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
ms.openlocfilehash: b333cbbe33b42709614376cf98be01111be967a2
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916810"
---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem – třída

Pomocí [CRichEditView –](../../mfc/reference/cricheditview-class.md) a [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)poskytuje funkce ovládacího prvku Rich Edit v rámci kontextu architektury zobrazení dokumentu knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CRichEditCntrItem::CRichEditCntrItem](#cricheditcntritem)|`CRichEditCntrItem` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|Aktivuje položku jako jiný typ.|

## <a name="remarks"></a>Poznámky

"Ovládací prvek" Rich Edit "je okno, ve kterém může uživatel text zadat a upravit. Textu lze přiřadit formátování znaků a odstavců a může obsahovat vložené objekty OLE. Ovládací prvky s bohatým úpravou poskytují programovací rozhraní pro formátování textu. Aplikace však musí implementovat všechny součásti uživatelského rozhraní, které jsou nezbytné k zpřístupnění operací formátování uživateli.

`CRichEditView`zachová text a formátuje charakteristiky textu. `CRichEditDoc`udržuje seznam položek klienta OLE, které jsou v zobrazení. `CRichEditCntrItem`poskytuje přístup na straně kontejneru k položce klienta OLE.

Tento běžný ovládací prvek systému Windows (a proto [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) a související třídy) je k dispozici pouze pro programy, které jsou spuštěny v systémech Windows 95/98 a Windows NT verze 3,51 a novější.

Příklad použití bohatě upravených položek kontejneru v aplikaci knihovny MFC naleznete v ukázkové aplikaci [WordPad](../../overview/visual-cpp-samples.md) .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrich. h

##  <a name="cricheditcntritem"></a>CRichEditCntrItem::CRichEditCntrItem

Voláním této funkce vytvoříte `CRichEditCntrItem` objekt a přidáte ho do kontejneru dokumentů.

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>Parametry

*preo*<br/>
Ukazatel na přeobjektovou strukturu, která popisuje položku OLE. [](/windows/desktop/api/richole/ns-richole-reobject) Nový `CRichEditCntrItem` objekt je vytvořen kolem této položky OLE. Pokud má *preo* hodnotu null, položka klienta je prázdná.

*pContainer*<br/>
Ukazatel na kontejnerový dokument, který bude obsahovat tuto položku. Pokud má *pContainer může* hodnotu null, je nutné explicitně volat [COleDocument:: AddItem](../../mfc/reference/coledocument-class.md#additem) , aby bylo možné tuto položku klienta přidat do dokumentu.

### <a name="remarks"></a>Poznámky

Tato funkce neprovádí žádnou inicializaci technologie OLE.

Další informace naleznete v tématu struktura [přeobjektů](/windows/desktop/api/richole/ns-richole-reobject) v Windows SDK.

##  <a name="synctoricheditobject"></a>  CRichEditCntrItem::SyncToRichEditObject

Voláním této funkce synchronizujte aspekt zařízení [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect), `CRichEditCntrltem` který určuje *REO*.

```
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>Parametry

*reo*<br/>
Odkaz na reobjektovou strukturu, která popisuje položku OLE. [](/windows/desktop/api/richole/ns-richole-reobject)

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Ukázka knihovny MFC v programu WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc – třída](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditView – třída](../../mfc/reference/cricheditview-class.md)
