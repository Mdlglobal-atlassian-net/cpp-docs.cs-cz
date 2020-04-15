---
title: COleCmdUI – třída
ms.date: 09/12/2018
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
helpviewer_keywords:
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
ms.openlocfilehash: 1b7a6b21a3ad778b4a5ca345b1aaf42875810e4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376268"
---
# <a name="colecmdui-class"></a>COleCmdUI – třída

Implementuje metodu knihovny MFC aktualizovat stav objektů `IOleCommandTarget`uživatelského rozhraní souvisejících s -řízený funkce aplikace.

## <a name="syntax"></a>Syntaxe

```
class COleCmdUI : public CCmdUI
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleCmdUI::COleCmdUI](#colecmdui)|Vytvoří `COleCmdUI` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleCmdUI::Povolit](#enable)|Nastaví nebo vymaže příkaz ový příznak příkazu.|
|[COleCmdUI::SetCheck](#setcheck)|Nastaví stav přepínače zapnutí/vypnutí.|
|[COleCmdUI::SetText](#settext)|Vrátí textový název nebo stavový řetězec příkazu.|

## <a name="remarks"></a>Poznámky

V aplikaci, která není povolena pro DocObjects, když uživatel zobrazí nabídku v aplikaci, knihovna MFC zpracuje UPDATE_COMMAND_UI notifcations. Každé oznámení je uveden [CCmdUI](../../mfc/reference/ccmdui-class.md) objekt, který lze manipulovat tak, aby odrážely stav určitého příkazu. Pokud je však aplikace povolena pro docobjects, knihovna `COleCmdUI` MFC zpracuje UPDATE_OLE_COMMAND_UI oznámení a přiřadí objekty.

`COleCmdUI`umožňuje DocObject přijímat příkazy, které pocházejí z uživatelského rozhraní jeho kontejneru (například FileNew, Open, Print a tak dále) a umožňuje kontejneru přijímat příkazy, které pocházejí z uživatelského rozhraní DocObject. Ačkoli `IDispatch` lze použít k odeslání stejné `IOleCommandTarget` příkazy, poskytuje jednodušší způsob dotazování a spuštění, protože spoléhá na standardní sadu příkazů, obvykle bez argumentů a žádné informace o typu je zapojen. `COleCmdUI`lze povolit, aktualizovat a nastavit další vlastnosti příkazů uživatelského rozhraní DocObject. Chcete-li příkaz vyvolat, zavolejte [cOleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd).

Další informace o docobjects naleznete v tématech [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) a [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CCmdUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdocobj.h

## <a name="colecmduicolecmdui"></a><a name="colecmdui"></a>COleCmdUI::COleCmdUI

Vytvoří `COleCmdUI` objekt přidružený k určitému příkazu uživatelského rozhraní.

```
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>Parametry

*rgCmds*<br/>
Seznam podporovaných příkazů přidružených k danému identifikátoru GUID. Struktura `OLECMD` přidruží příkazy k příznakům příkazu.

*cCmds*<br/>
Počet příkazů v *rgCmds*.

*pSkupina*<br/>
Ukazatel na identifikátor GUID, který identifikuje sadu příkazů.

### <a name="remarks"></a>Poznámky

Objekt `COleCmdUI` poskytuje programové rozhraní pro aktualizaci objektů uživatelského rozhraní DocObject, jako jsou položky nabídky nebo tlačítka ovládacího panelu. Objekty uživatelského rozhraní lze povolit, zakázat, zkontrolovat a/nebo vymazat prostřednictvím objektu. `COleCmdUI`

## <a name="colecmduienable"></a><a name="enable"></a>COleCmdUI::Povolit

Voláním této funkce nastavte příznak `COleCmdUI` příkazu objektu na OLECOMDF_ENABLED, který informuje rozhraní, že příkaz je k dispozici a povolen, nebo chcete vymazat příznak příkazu.

```
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>Parametry

*Bon*<br/>
Označuje, zda má `COleCmdUI` být povolen nebo zakázán příkaz přidružený k objektu. Nenulová umožňuje příkaz; 0 zakáže příkaz.

## <a name="colecmduisetcheck"></a><a name="setcheck"></a>COleCmdUI::SetCheck

Voláním této funkce nastavte stav příkazu zapnutí/vypnutí.

```
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parametry

*nKontrola*<br/>
Hodnota určující stav pro nastavení příkazu zapnutí/vypnutí. Hodnoty jsou:

|Hodnota|Popis|
|-----------|-----------------|
|**1**|Nastaví příkaz na zapnuto.|
|**2**|Nastaví příkaz na neurčitý; stav nelze určit, protože atribut tohoto příkazu je v zapnutém i vypnutém stavu v příslušném výběru.|
|jakákoli jiná hodnota|Nastaví vypnutý příkaz.|

## <a name="colecmduisettext"></a><a name="settext"></a>COleCmdUI::SetText

Volánítéto funkce vrátí textový název nebo stavový řetězec pro příkaz.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Ukazatel na text, který má být použit s příkazem.

## <a name="see-also"></a>Viz také

[CCmdUI – třída](../../mfc/reference/ccmdui-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
