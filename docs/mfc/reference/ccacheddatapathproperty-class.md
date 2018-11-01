---
title: Ccacheddatapathproperty – třída
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
ms.openlocfilehash: 1605d5fe1549ba5172f61583cce586a353c2ab56
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485654"
---
# <a name="ccacheddatapathproperty-class"></a>Ccacheddatapathproperty – třída

Implementuje ovládacího prvku OLE asynchronně převedený a uložili do mezipaměti v paměti souboru vlastnost.

## <a name="syntax"></a>Syntaxe

```
class CCachedDataPathProperty : public CDataPathProperty
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|Vytvoří `CCachedDataPathProperty` objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile` objekt ve kterém ukládání dat do mezipaměti.|

## <a name="remarks"></a>Poznámky

Paměťového souboru je uložené v paměti RAM, nikoli na disk a je užitečné pro rychlé dočasné přenosy.

Spolu s `CAysncMonikerFile` a `CDataPathProperty`, `CCachedDataPathProperty` poskytuje funkce pro používání asynchronních zástupných názvů v ovládacích prvků OLE. S `CCachedDataPathProperty` objekty, budete moct asynchronně přenášet data ze zdroje adresu URL nebo soubor a uložte ho do souboru paměti prostřednictvím `m_Cache` veřejné proměnné. Všechna data uložená v souboru paměti a není nutné přepsat [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) Pokud nechcete, podívejte se na oznámení a reagovat. Například pokud přenášíte velké. Soubor ve formátu GIF a chcete sdělit svůj ovládací prvek, že dorazila více dat a jeho by měl překreslit, přepsat `OnDataAvailable` aby oznámení.

Třída `CCachedDataPathProperty` je odvozen z `CDataPathProperty`.

Další informace o tom, jak použít asynchronní monikery a ovládací prvky ActiveX v internetových aplikací naleznete v následujících tématech:

- [Internet první kroky: Ovládací prvky ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [Internetu první kroky: Asynchronní Monikery](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cfile –](../../mfc/reference/cfile-class.md)

[Colestreamfile –](../../mfc/reference/colestreamfile-class.md)

[Cmonikerfile –](../../mfc/reference/cmonikerfile-class.md)

[Casyncmonikerfile –](../../mfc/reference/casyncmonikerfile-class.md)

[Cdatapathproperty –](../../mfc/reference/cdatapathproperty-class.md)

`CCachedDataPathProperty`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

##  <a name="ccacheddatapathproperty"></a>  CCachedDataPathProperty::CCachedDataPathProperty

Vytvoří `CCachedDataPathProperty` objektu.

```
CCachedDataPathProperty(COleControl* pControl = NULL);

CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parametry

*pControl*<br/>
Ukazatel na objekt ovládacího prvku ActiveX, který se má přidružit to `CCachedDataPathProperty` objektu.

*lpszPath*<br/>
Cesty, která může být absolutní nebo relativní, je použít k vytvoření asynchronní monikeru, který odkazuje na aktuální absolutní umístění vlastnost. `CCachedDataPathProperty` pomocí adresy URL, ne názvy souborů. Pokud chcete, aby `CCachedDataPathProperty` objektu pro soubor, předřaďte file:// k cestě.

### <a name="remarks"></a>Poznámky

`COleControl` Objekt, který odkazuje *pControl* používá [otevřít](../../mfc/reference/cdatapathproperty-class.md#open) a načíst z odvozených tříd. Pokud *pControl* má hodnotu NULL, ovládací prvek použitý s `Open` by měla být nastavena s [SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol). Pokud *lpszPath* má hodnotu NULL, můžete předat cestu prostřednictvím `Open` nebo ji nastavte [SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath).

##  <a name="m_cache"></a>  CCachedDataPathProperty::m_Cache

Obsahuje název třídy paměti souboru, do kterého se data uložená v mezipaměti.

```
CMemFile m_Cache;
```

### <a name="remarks"></a>Poznámky

Paměťového souboru je uložené v paměti RAM, nikoli na disku.

## <a name="see-also"></a>Viz také

[CDataPathProperty – třída](../../mfc/reference/cdatapathproperty-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDataPathProperty – třída](../../mfc/reference/cdatapathproperty-class.md)
