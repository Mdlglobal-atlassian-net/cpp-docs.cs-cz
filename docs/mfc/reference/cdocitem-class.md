---
title: Cdocitem – třída
ms.date: 11/04/2016
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
helpviewer_keywords:
- CDocItem [MFC], GetDocument
- CDocItem [MFC], IsBlank
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
ms.openlocfilehash: cf854bbc99ebeee55ae130b747c77fd7fe52f8d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437099"
---
# <a name="cdocitem-class"></a>Cdocitem – třída

Základní třída pro položky dokumentu, které jsou součástí dat dokumentu.

## <a name="syntax"></a>Syntaxe

```
class CDocItem : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDocItem::GetDocument](#getdocument)|Vrátí dokument, který obsahuje položku.|
|[CDocItem::IsBlank](#isblank)|Určuje, zda položka obsahuje všechny informace.|

## <a name="remarks"></a>Poznámky

`CDocItem` objekty se používají pro reprezentaci položky OLE v dokumentech klienta i serveru.

Další informace najdete v článku [kontejnery: Implementace kontejneru](../../mfc/containers-implementing-a-container.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocItem`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

##  <a name="getdocument"></a>  CDocItem::GetDocument

Voláním této funkce získáte dokumentu, který obsahuje položku.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dokument, který obsahuje položky; Hodnota NULL, pokud položka není součástí dokumentu.

### <a name="remarks"></a>Poznámky

Tato funkce je v odvozených třídách přepsána [COleClientItem](../../mfc/reference/coleclientitem-class.md) a [odvozenou třídu COleServerItem](../../mfc/reference/coleserveritem-class.md), vrací ukazatel na buď [coledocument –](../../mfc/reference/coledocument-class.md), [ Colelinkingdoc –](../../mfc/reference/colelinkingdoc-class.md), nebo [coleserverdoc –](../../mfc/reference/coleserverdoc-class.md) objektu.

##  <a name="isblank"></a>  CDocItem::IsBlank

Volá se rozhraním, když dojde k výchozí serializace.

```
virtual BOOL IsBlank() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud položka neobsahuje žádné informace o; jinak 0.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `CDocItem` objekty nejsou prázdné. [COleClientItem](../../mfc/reference/coleclientitem-class.md) objekty jsou prázdné někdy, protože vyplývají přímo ze `CDocItem`. Ale [odvozenou třídu COleServerItem](../../mfc/reference/coleserveritem-class.md) objekty jsou vždy prázdná. Ve výchozím nastavení, OLE – aplikace, který obsahuje `COleClientItem` objekty, které mají žádné x nebo y rozsahu se serializují. To se provádí tak, že vrací hodnotu TRUE z přepsání `IsBlank` Pokud položka neobsahuje žádné x nebo y rozsahu.

Tato funkce přepište, pokud chcete provádět další akce během serializace.

## <a name="see-also"></a>Viz také

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDocument – třída](../../mfc/reference/coledocument-class.md)<br/>
[COleServerItem – třída](../../mfc/reference/coleserveritem-class.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)
