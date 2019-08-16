---
title: CRichEditDoc – třída
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
ms.openlocfilehash: def0c55ff1faf12729226aa445c9614119c546c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502679"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc – třída

Pomocí [CRichEditView –](../../mfc/reference/cricheditview-class.md) a [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)poskytuje funkce ovládacího prvku Rich Edit v rámci kontextu architektury zobrazení dokumentu knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|Volá se, aby se provedlo vyčištění dokumentu.|
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|Určuje, zda by měl vstup a výstup streamu zahrnovat informace o formátování.|
|[CRichEditDoc:: GetView](#getview)|Načte objekt asssociated [CRichEditView –](../../mfc/reference/cricheditview-class.md) .|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CRichEditDoc::m_bRTF](#m_brtf)|Určuje, zda má vstupní/výstupní datový proud zahrnovat formátování.|

## <a name="remarks"></a>Poznámky

"Ovládací prvek" Rich Edit "je okno, ve kterém může uživatel text zadat a upravit. Textu lze přiřadit formátování znaků a odstavců a může obsahovat vložené objekty OLE. Ovládací prvky s bohatým úpravou poskytují programovací rozhraní pro formátování textu. Aplikace však musí implementovat všechny součásti uživatelského rozhraní, které jsou nezbytné k zpřístupnění operací formátování uživateli.

`CRichEditView`zachová text a formátuje charakteristiky textu. `CRichEditDoc`udržuje seznam položek klienta, které jsou v zobrazení. `CRichEditCntrItem`poskytuje přístup na straně kontejneru k položkám klienta OLE.

Tento běžný ovládací prvek systému Windows (a proto [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) a související třídy) je k dispozici pouze pro programy, které jsou spuštěny v systémech Windows 95/98 a Windows NT verze 3,51 a novější.

Příklad použití dokumentu s bohatou úpravou v aplikaci knihovny MFC naleznete v ukázkové aplikaci [WordPad](../../overview/visual-cpp-samples.md) .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[Objektu CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrich. h

##  <a name="createclientitem"></a>CRichEditDoc:: CreateClientItem

Voláním této funkce vytvoříte `CRichEditCntrItem` objekt a přidáte ho do tohoto dokumentu.

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>Parametry

*preo*<br/>
Ukazatel na přeobjektovou strukturu, která popisuje položku OLE. [](/windows/win32/api/richole/ns-richole-reobject) Nový `CRichEditCntrItem` objekt je vytvořen kolem této položky OLE. Pokud má *preo* hodnotu null, nová položka klienta je prázdná.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nový objekt [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) , který byl přidán do tohoto dokumentu.

### <a name="remarks"></a>Poznámky

Tato funkce neprovádí žádnou inicializaci technologie OLE.

Další informace naleznete v tématu struktura [přeobjektů](/windows/win32/api/richole/ns-richole-reobject) v Windows SDK.

##  <a name="getstreamformat"></a>CRichEditDoc:: GetStreamFormat

Voláním této funkce určíte textový formát pro streamování obsahu s bohatou úpravou.

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>Návratová hodnota

Jeden z následujících příznaků:

- SF_TEXT označuje, že ovládací prvek RichEdit pro úpravy neudržuje informace o formátování.

- SF_RTF označuje, že ovládací prvek RichEdit pro úpravy udržuje informace o formátování.

### <a name="remarks"></a>Poznámky

Vrácená hodnota je založena na datovém členu [m_bRTF](#m_brtf) . Tato funkce vrátí SF_RTF, `m_bRTF` Pokud je true, jinak SF_TEXT.

##  <a name="getview"></a>CRichEditDoc:: GetView

Voláním této funkce získáte přístup k objektu [CRichEditView –](../../mfc/reference/cricheditview-class.md) přidruženému `CRichEditDoc` k tomuto objektu.

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CRichEditView` objekt přidružený k dokumentu.

### <a name="remarks"></a>Poznámky

Text a informace o formátování jsou obsaženy v rámci `CRichEditView` objektu. `CRichEditDoc` Objekt udržuje položky OLE pro serializaci. Pro každý `CRichEditView` `CRichEditDoc`by měl být jenom jeden.

##  <a name="m_brtf"></a>  CRichEditDoc::m_bRTF

V případě hodnoty TRUE označuje, že [CRichEditCtrl:: streamin](../../mfc/reference/cricheditctrl-class.md#streamin) a [CRichEditCtrl:: Stream](../../mfc/reference/cricheditctrl-class.md#streamout) by měl ukládat charakteristiky formátování odstavců a znaků.

```
BOOL m_bRTF;
```

## <a name="see-also"></a>Viz také:

[Ukázka knihovny MFC v programu WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleServerDoc – třída](../../mfc/reference/coleserverdoc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRichEditView – třída](../../mfc/reference/cricheditview-class.md)<br/>
[CRichEditCntrItem – třída](../../mfc/reference/cricheditcntritem-class.md)<br/>
[COleDocument – třída](../../mfc/reference/coledocument-class.md)<br/>
[CRichEditCtrl – třída](../../mfc/reference/cricheditctrl-class.md)
