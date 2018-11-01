---
title: Cricheditcntritem – třída
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
ms.openlocfilehash: 4683e0ea4a56e6766c039b2fcb858a54e28d14ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443339"
---
# <a name="cricheditcntritem-class"></a>Cricheditcntritem – třída

S [cricheditview –](../../mfc/reference/cricheditview-class.md) a [cricheditdoc –](../../mfc/reference/cricheditdoc-class.md), poskytuje funkce pro ovládací prvek RTF v rámci kontextu architektury zobrazení dokumentu MFC.

## <a name="syntax"></a>Syntaxe

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CRichEditCntrItem::CRichEditCntrItem](#cricheditcntritem)|Vytvoří `CRichEditCntrItem` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|Aktivuje položku jako jiného typu.|

## <a name="remarks"></a>Poznámky

"Ovládacího prvku rich edit" je okno, ve kterém můžete uživatele zadat a upravit text. Text je možné přiřadit formátování znaků a odstavců a může obsahovat vložené objekty OLE. Bohaté ovládacích prvcích pro úpravy poskytují programovací rozhraní pro formátování textu. Však musí aplikace implementovat součásti potřebné k zajištění operací formátování pro uživatele k dispozici žádné uživatelského rozhraní.

`CRichEditView` udržuje textu a formátování vlastnosti textu. `CRichEditDoc` udržuje seznam klientské položky OLE, které jsou v zobrazení. `CRichEditCntrItem` poskytuje kontejner straně přístup k klientskou položku OLE.

Tento ovládací prvek Windows běžné (a tedy [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) a související třídy) je dostupná jenom pro programy spuštěné v rámci Windows 95/98 a Windows NT verze 3.51 a vyšší.

Příklad použití RichEdit kontejner položek v aplikaci knihovny MFC, najdete v článku [WORDPAD](../../visual-cpp-samples.md) ukázkovou aplikaci.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[Cdocitem –](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrich.h

##  <a name="cricheditcntritem"></a>  CRichEditCntrItem::CRichEditCntrItem

Volání této funkce můžete vytvořit `CRichEditCntrItem` objektu a přidejte ji do dokumentu kontejneru.

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>Parametry

*preo*<br/>
Ukazatel [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) struktura, která popisuje položky OLE. Nové `CRichEditCntrItem` objektu je postavena na tuto položku OLE. Pokud *preo* má hodnotu NULL, položka klienta je prázdná.

*pContainer*<br/>
Ukazatel na dokument kontejneru, který bude obsahovat této položky. Pokud *pContainer* má hodnotu NULL, je nutné explicitně volat [COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem) na tuto položku klienta přidat do dokumentu.

### <a name="remarks"></a>Poznámky

Tato funkce není udělat všechny inicializace technologie OLE.

Další informace najdete v tématu [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) struktura v sadě Windows SDK.

##  <a name="synctoricheditobject"></a>  CRichEditCntrItem::SyncToRichEditObject

Voláním této funkce synchronizovat zařízení aspekt [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect), to `CRichEditCntrltem` na klíči určenému *Znov*.

```
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>Parametry

*Znov*<br/>
Odkaz [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) struktura, která popisuje položky OLE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC WORDPAD](../../visual-cpp-samples.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc – třída](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditView – třída](../../mfc/reference/cricheditview-class.md)
