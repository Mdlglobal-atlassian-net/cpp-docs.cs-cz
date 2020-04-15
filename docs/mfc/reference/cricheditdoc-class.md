---
title: Třída CrichEditDoc
ms.date: 11/04/2016
f1_keywords:
- CRichEditDoc
- AFXRICH/CRichEditDoc
- AFXRICH/CRichEditDoc::CreateClientItem
- AFXRICH/CRichEditDoc::GetStreamFormat
- AFXRICH/CRichEditDoc::GetView
- AFXRICH/CRichEditDoc::m_bRTF
helpviewer_keywords:
- CRichEditDoc [MFC], CreateClientItem
- CRichEditDoc [MFC], GetStreamFormat
- CRichEditDoc [MFC], GetView
- CRichEditDoc [MFC], m_bRTF
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
ms.openlocfilehash: 587cf65543e24e586fb8b2336481d6e841473134
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368261"
---
# <a name="cricheditdoc-class"></a>Třída CrichEditDoc

S [CRichEditView](../../mfc/reference/cricheditview-class.md) a [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), poskytuje funkce rich edit control v kontextu architektury zobrazení dokumentu knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|Nazývá se provést vyčištění dokumentu.|
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|Označuje, zda má vstup datového proudu a výstup obsahovat informace o formátování.|
|[CRichEditDoc::GetView](#getview)|Načte asssociated [CRichEditView](../../mfc/reference/cricheditview-class.md) objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CRichEditDoc::m_bRTF](#m_brtf)|Označuje, zda má vstupně-tovitý proud obsahovat formátování.|

## <a name="remarks"></a>Poznámky

"Rich edit control" je okno, ve kterém může uživatel zadávat a upravovat text. Text může být přiřazen k formátování znaků a odstavců a může obsahovat vložené objekty OLE. Ovládací prvky pro úpravy rich poskytují programovací rozhraní pro formátování textu. Aplikace však musí implementovat všechny součásti uživatelského rozhraní nezbytné k tomu, aby byly operace formátování dostupné uživateli.

`CRichEditView`zachová text a formátování charakteristiky textu. `CRichEditDoc`udržuje seznam klientských položek, které jsou v zobrazení. `CRichEditCntrItem`poskytuje přístup na straně kontejneru k položkám klienta OLE.

Tento ovládací prvek Windows Common (a tedy [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) a související třídy) je k dispozici pouze pro programy spuštěné v systémech Windows 95/98 a Windows NT verze 3.51 a novější.

Příklad použití dokumentu s bohatou úpravou v aplikaci knihovny MFC naleznete v ukázkové aplikaci [wordpadu.](../../overview/visual-cpp-samples.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[CDokument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrich.h

## <a name="cricheditdoccreateclientitem"></a><a name="createclientitem"></a>CRichEditDoc::CreateClientItem

Voláním této funkce `CRichEditCntrItem` vytvořte objekt a přidejte jej do tohoto dokumentu.

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>Parametry

*preo*<br/>
Ukazatel na strukturu [REOBJECT,](/windows/win32/api/richole/ns-richole-reobject) která popisuje položku OLE. Nový `CRichEditCntrItem` objekt je vytvořen kolem této položky OLE. Pokud *preo* je NULL, nová položka klienta je prázdný.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nový [cRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objekt, který byl přidán do tohoto dokumentu.

### <a name="remarks"></a>Poznámky

Tato funkce neprovádí žádnou inicializaci OLE.

Další informace naleznete v části Struktura [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) v sadě Windows SDK.

## <a name="cricheditdocgetstreamformat"></a><a name="getstreamformat"></a>CRichEditDoc::GetStreamFormat

Volání této funkce k určení formátu textu pro streamování obsahu bohaté úpravy.

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>Návratová hodnota

Jeden z následujících příznaků:

- SF_TEXT Označuje, že ovládací prvek rich edit neudržuje informace o formátování.

- SF_RTF Označuje, že ovládací prvek rich edit udržuje informace o formátování.

### <a name="remarks"></a>Poznámky

Vrácená hodnota je založena na [m_bRTF](#m_brtf) datového člena. Tato funkce vrátí `m_bRTF` SF_RTF pokud je TRUE; jinak SF_TEXT.

## <a name="cricheditdocgetview"></a><a name="getview"></a>CRichEditDoc::GetView

Volání této funkce pro přístup k [cRichEditView](../../mfc/reference/cricheditview-class.md) objekt přidružený k tomuto `CRichEditDoc` objektu.

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CRichEditView` objekt přidružený k dokumentu.

### <a name="remarks"></a>Poznámky

Informace o textu a formátování jsou `CRichEditView` obsaženy v objektu. Objekt `CRichEditDoc` udržuje položky OLE pro serializaci. Pro každého `CRichEditDoc`by `CRichEditView` měl být pouze jeden .

## <a name="cricheditdocm_brtf"></a><a name="m_brtf"></a>CRichEditDoc::m_bRTF

Když TRUE, označuje, že [CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin) a [CRichEditCtrl::StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout) by měl ukládat body a znak formátování charakteristiky.

```
BOOL m_bRTF;
```

## <a name="see-also"></a>Viz také

[MFC Ukázka WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[Třída COleServerDoc](../../mfc/reference/coleserverdoc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRichEditView – třída](../../mfc/reference/cricheditview-class.md)<br/>
[Třída CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)<br/>
[Třída COleDocument](../../mfc/reference/coledocument-class.md)<br/>
[CRichEditCtrl – třída](../../mfc/reference/cricheditctrl-class.md)
