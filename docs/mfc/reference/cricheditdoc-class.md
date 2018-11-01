---
title: Cricheditdoc – třída
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
ms.openlocfilehash: 8e97b17a3620d75660a5ac2109bc440f8ad27b16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453454"
---
# <a name="cricheditdoc-class"></a>Cricheditdoc – třída

S [cricheditview –](../../mfc/reference/cricheditview-class.md) a [cricheditcntritem –](../../mfc/reference/cricheditcntritem-class.md), poskytuje funkce pro ovládací prvek RTF v rámci kontextu architektury zobrazení dokumentu MFC.

## <a name="syntax"></a>Syntaxe

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|Volá se, aby, vyčistěte dokumentu.|
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|Určuje, zda datový proud vstup a výstup by měl obsahovat informace o formátování.|
|[CRichEditDoc::GetView](#getview)|Načte asssociated [cricheditview –](../../mfc/reference/cricheditview-class.md) objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CRichEditDoc::m_bRTF](#m_brtf)|Určuje, zda by měl obsahovat datový proud vstupně-výstupní operace formátování.|

## <a name="remarks"></a>Poznámky

"Ovládacího prvku rich edit" je okno, ve kterém můžete uživatele zadat a upravit text. Text je možné přiřadit formátování znaků a odstavců a může obsahovat vložené objekty OLE. Bohaté ovládacích prvcích pro úpravy poskytují programovací rozhraní pro formátování textu. Však musí aplikace implementovat součásti potřebné k zajištění operací formátování pro uživatele k dispozici žádné uživatelského rozhraní.

`CRichEditView` udržuje textu a formátování vlastnosti textu. `CRichEditDoc` udržuje seznam klientské položky, které jsou v zobrazení. `CRichEditCntrItem` poskytuje kontejner straně přístup ke klientské položky OLE.

Tento ovládací prvek Windows běžné (a tedy [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) a související třídy) je dostupná jenom pro programy spuštěné v rámci Windows 95/98 a Windows NT verze 3.51 a vyšší.

Příklad použití RichEdit dokumentu v aplikaci knihovny MFC, najdete v článku [WORDPAD](../../visual-cpp-samples.md) ukázkovou aplikaci.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[Coledocument –](../../mfc/reference/coledocument-class.md)

[Colelinkingdoc –](../../mfc/reference/colelinkingdoc-class.md)

[Coleserverdoc –](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrich.h

##  <a name="createclientitem"></a>  CRichEditDoc::CreateClientItem

Volání této funkce můžete vytvořit `CRichEditCntrItem` objektu a přidejte ho do tohoto dokumentu.

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>Parametry

*preo*<br/>
Ukazatel [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) struktura, která popisuje položky OLE. Nové `CRichEditCntrItem` objektu je postavena na tuto položku OLE. Pokud *preo* má hodnotu NULL, nová položka klienta je prázdná.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na novou [cricheditcntritem –](../../mfc/reference/cricheditcntritem-class.md) objekt, který byl přidán do tohoto dokumentu.

### <a name="remarks"></a>Poznámky

Tato funkce není udělat všechny inicializace technologie OLE.

Další informace najdete v tématu [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) struktura v sadě Windows SDK.

##  <a name="getstreamformat"></a>  CRichEditDoc::GetStreamFormat

Voláním této funkce k určení formátu textu pro streamování obsahu RichEdit.

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>Návratová hodnota

Jeden z následujících příznaků:

- SF_TEXT označuje, že získáte bohaté ovládací prvek textové pole neumožňuje spravovat informace o formátování.

- SF_RTF označuje, že pro úpravy s formátováním ovládací prvek Udržovat informace o formátování.

### <a name="remarks"></a>Poznámky

Návratová hodnota je založena na [m_bRTF](#m_brtf) datový člen. Tato funkce vrací SF_RTF Pokud `m_bRTF` je TRUE; v opačném případě SF_TEXT.

##  <a name="getview"></a>  CRichEditDoc::GetView

Voláním této funkce pro přístup k [cricheditview –](../../mfc/reference/cricheditview-class.md) objekt přidružený k tomuto `CRichEditDoc` objektu.

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CRichEditView` objekt přidružený k dokumentu.

### <a name="remarks"></a>Poznámky

Souhrnný text a informace o formátování `CRichEditView` objektu. `CRichEditDoc` Udržuje položky OLE pro serializaci objektu. Měl by existovat pouze jeden `CRichEditView` pro každou `CRichEditDoc`.

##  <a name="m_brtf"></a>  CRichEditDoc::m_bRTF

V případě hodnoty TRUE označuje, že [CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin) a [CRichEditCtrl::StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout) měli uložit charakteristiky formátování znaků a odstavců.

```
BOOL m_bRTF;
```

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC WORDPAD](../../visual-cpp-samples.md)<br/>
[COleServerDoc – třída](../../mfc/reference/coleserverdoc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRichEditView – třída](../../mfc/reference/cricheditview-class.md)<br/>
[CRichEditCntrItem – třída](../../mfc/reference/cricheditcntritem-class.md)<br/>
[COleDocument – třída](../../mfc/reference/coledocument-class.md)<br/>
[CRichEditCtrl – třída](../../mfc/reference/cricheditctrl-class.md)
