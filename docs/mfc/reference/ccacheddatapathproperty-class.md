---
title: CCachedDataPathProperty – třída
ms.date: 11/04/2016
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
ms.openlocfilehash: ebab34433f23b119e3444b3eaa8b0ad6313555af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352367"
---
# <a name="ccacheddatapathproperty-class"></a>CCachedDataPathProperty – třída

Implementuje vlastnost ovládacího prvku OLE přenesenou asynchronně a uloženou do mezipaměti v paměťovém souboru.

## <a name="syntax"></a>Syntaxe

```
class CCachedDataPathProperty : public CDataPathProperty
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|Vytvoří `CCachedDataPathProperty` objekt.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile`objekt, do kterého chcete ukládat data do mezipaměti.|

## <a name="remarks"></a>Poznámky

Paměťový soubor je uložen v paměti RAM, nikoli na disku a je užitečný pro rychlé dočasné přenosy.

Spolu `CAysncMonikerFile` s `CDataPathProperty` `CCachedDataPathProperty` a , poskytuje funkce pro použití asynchronních zástupných názvů v ovládacích prvcích OLE. S `CCachedDataPathProperty` objekty můžete přenášet data asynchronně z adresy URL nebo zdroje souboru `m_Cache` a ukládat je do paměťového souboru prostřednictvím veřejné proměnné. Všechna data jsou uložena v paměťovém souboru a není nutné přepsat [OnDataAvailable,](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) pokud chcete sledovat oznámení a reagovat. Například pokud přenášíte velké . GIF soubor a chcete upozornit svůj ovládací prvek, že dorazilo `OnDataAvailable` více dat a mělo by se překreslit, přepsat, aby se oznámení.

Třída `CCachedDataPathProperty` je odvozena `CDataPathProperty`od .

Další informace o použití asynchronních zástupných názvů a ovládacích prvků ActiveX v internetových aplikacích naleznete v následujících tématech:

- [První kroky Internetu: Ovládací prvky ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [První kroky internetu: Asynchronní přezdívky](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Soubor C](../../mfc/reference/cfile-class.md)

[Soubor COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[Soubor CMoniker](../../mfc/reference/cmonikerfile-class.md)

[Soubor CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

[CDataPathVlastnost](../../mfc/reference/cdatapathproperty-class.md)

`CCachedDataPathProperty`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

## <a name="ccacheddatapathpropertyccacheddatapathproperty"></a><a name="ccacheddatapathproperty"></a>CCachedDataPathProperty::CCachedDataPathProperty

Vytvoří `CCachedDataPathProperty` objekt.

```
CCachedDataPathProperty(COleControl* pControl = NULL);

CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parametry

*pOvládací prvek*<br/>
Ukazatel na objekt ovládacího prvku ActiveX, který má být přidružen k tomuto `CCachedDataPathProperty` objektu.

*lpszPath*<br/>
Cesta, která může být absolutní nebo relativní, slouží k vytvoření asynchronní zástupný název, který odkazuje na skutečné absolutní umístění vlastnosti. `CCachedDataPathProperty`používá adresy URL, nikoli názvy souborů. Pokud chcete `CCachedDataPathProperty` objekt pro soubor, předřadit file:// na cestu.

### <a name="remarks"></a>Poznámky

Objekt, `COleControl` na který *pControl* [poukazuje,](../../mfc/reference/cdatapathproperty-class.md#open) je používán otevřenou a načtenodvozenou odvozenými třídami. Pokud *pControl* je NULL, `Open` ovládací prvek používaný s by měl být nastaven s [SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol). Pokud *lpszPath* je NULL, můžete předat `Open` cestu přes nebo nastavit pomocí [SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath).

## <a name="ccacheddatapathpropertym_cache"></a><a name="m_cache"></a>CCachedDataPathProperty::m_Cache

Obsahuje název třídy paměťového souboru, do kterého jsou data ukládána do mezipaměti.

```
CMemFile m_Cache;
```

### <a name="remarks"></a>Poznámky

Paměťový soubor je uložen v paměti RAM, nikoli na disku.

## <a name="see-also"></a>Viz také

[CDataPathProperty – třída](../../mfc/reference/cdatapathproperty-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDataPathProperty – třída](../../mfc/reference/cdatapathproperty-class.md)
