---
title: CDocItem – třída
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
ms.openlocfilehash: 438bc2a03239946dbfca53d5f2989c731b682ab0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375626"
---
# <a name="cdocitem-class"></a>CDocItem – třída

Základní třída pro položky dokumentu, které jsou součástí dat dokumentu.

## <a name="syntax"></a>Syntaxe

```
class CDocItem : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDocItem::GetDocument](#getdocument)|Vrátí dokument, který obsahuje položku.|
|[CDocItem::IsBlank](#isblank)|Určuje, zda položka obsahuje nějaké informace.|

## <a name="remarks"></a>Poznámky

`CDocItem`objekty se používají k reprezentaci položek OLE v klientských i serverových dokumentech.

Další informace naleznete v článku [Kontejnery: Implementace kontejneru](../../mfc/containers-implementing-a-container.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

`CDocItem`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="cdocitemgetdocument"></a><a name="getdocument"></a>CDocItem::GetDocument

Volání této funkce získat dokument, který obsahuje položku.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dokument, který obsahuje položku; NULL, pokud položka není součástí dokumentu.

### <a name="remarks"></a>Poznámky

Tato funkce je přepsána v odvozených třídách [COleClientItem](../../mfc/reference/coleclientitem-class.md) a [COleServerItem](../../mfc/reference/coleserveritem-class.md), vrací ukazatel buď [cOleDocument](../../mfc/reference/coledocument-class.md), [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)nebo [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) objektu.

## <a name="cdocitemisblank"></a><a name="isblank"></a>CDocItem::IsBlank

Volat v rámci při výchozí serializace dojde.

```
virtual BOOL IsBlank() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud položka neobsahuje žádné informace; jinak 0.

### <a name="remarks"></a>Poznámky

Ve výchozím `CDocItem` nastavení nejsou objekty prázdné. [COleClientItem](../../mfc/reference/coleclientitem-class.md) objekty jsou někdy prázdné, protože jsou odvozeny přímo z `CDocItem`. Objekty [COleServerItem](../../mfc/reference/coleserveritem-class.md) jsou však vždy prázdné. Ve výchozím nastavení jsou `COleClientItem` aplikace OLE obsahující objekty, které nemají rozsah x nebo y, serializovány. To se provádí vrácením TRUE z `IsBlank` přepsání, pokud položka nemá žádný rozsah x nebo y.

Přepsat tuto funkci, pokud chcete implementovat další akce během serializace.

## <a name="see-also"></a>Viz také

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída COleDocument](../../mfc/reference/coledocument-class.md)<br/>
[COleServerItem – třída](../../mfc/reference/coleserveritem-class.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)
