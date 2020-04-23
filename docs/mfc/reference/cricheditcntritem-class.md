---
title: Třída CRichEditCntrItem
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
ms.openlocfilehash: 7b566fe7f1c0667dbcdb4976f79cd2e1597f48f6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752766"
---
# <a name="cricheditcntritem-class"></a>Třída CRichEditCntrItem

S [CRichEditView](../../mfc/reference/cricheditview-class.md) a [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)poskytuje funkce bohaté upravit řízení v kontextu architektury zobrazení dokumentu knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CRichEditCntrItem::CRichEditCntrItem](#cricheditcntritem)|Vytvoří `CRichEditCntrItem` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|Aktivuje položku jako jiný typ.|

## <a name="remarks"></a>Poznámky

"Rich edit control" je okno, ve kterém může uživatel zadávat a upravovat text. Text může být přiřazen k formátování znaků a odstavců a může obsahovat vložené objekty OLE. Ovládací prvky pro úpravy rich poskytují programovací rozhraní pro formátování textu. Aplikace však musí implementovat všechny součásti uživatelského rozhraní nezbytné k tomu, aby byly operace formátování dostupné uživateli.

`CRichEditView`zachová text a formátování charakteristiky textu. `CRichEditDoc`udržuje seznam položek klienta OLE, které jsou v zobrazení. `CRichEditCntrItem`poskytuje přístup na straně kontejneru k položce klienta OLE.

Tento ovládací prvek Windows Common (a tedy [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) a související třídy) je k dispozici pouze pro programy spuštěné v systémech Windows 95/98 a Windows NT verze 3.51 a novější.

Příklad použití položek kontejneru s bohatou úpravou v aplikaci knihovny MFC naleznete v ukázkové aplikaci [wordpadu.](../../overview/visual-cpp-samples.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrich.h

## <a name="cricheditcntritemcricheditcntritem"></a><a name="cricheditcntritem"></a>CRichEditCntrItem::CRichEditCntrItem

Volání této funkce `CRichEditCntrItem` k vytvoření objektu a jeho přidání do dokumentu kontejneru.

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>Parametry

*preo*<br/>
Ukazatel na strukturu [REOBJECT,](/windows/win32/api/richole/ns-richole-reobject) která popisuje položku OLE. Nový `CRichEditCntrItem` objekt je vytvořen kolem této položky OLE. Pokud *preo* je NULL, položka klienta je prázdný.

*pKontejner*<br/>
Ukazatel na dokument kontejneru, který bude obsahovat tuto položku. Pokud *pContainer* je NULL, musíte explicitně volat [COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem) přidat tuto položku klienta do dokumentu.

### <a name="remarks"></a>Poznámky

Tato funkce neprovádí žádnou inicializaci OLE.

Další informace naleznete v části Struktura [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) v sadě Windows SDK.

## <a name="cricheditcntritemsynctoricheditobject"></a><a name="synctoricheditobject"></a>CRichEditCntrItem::SyncToRichEditObject

Volání této funkce pro synchronizaci aspekt zařízení, `CRichEditCntrltem` [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), to, že zadaný *reo*.

```cpp
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>Parametry

*Reo*<br/>
Odkaz na strukturu [REOBJECT,](/windows/win32/api/richole/ns-richole-reobject) která popisuje položku OLE.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[MFC Ukázka WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CrichEditDoc](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditView – třída](../../mfc/reference/cricheditview-class.md)
