---
title: Colecmdui – třída
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
ms.openlocfilehash: 5dc4e9504805146a9eff0f5ab937868226e4516e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148507"
---
# <a name="colecmdui-class"></a>Colecmdui – třída

Implementuje metodu knihovny MFC pro aktualizaci stavu objektů uživatelského rozhraní související s `IOleCommandTarget`-driven funkce vaší aplikace.

## <a name="syntax"></a>Syntaxe

```
class COleCmdUI : public CCmdUI
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleCmdUI::COleCmdUI](#colecmdui)|Vytvoří `COleCmdUI` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleCmdUI::Enable](#enable)|Nastaví nebo vymaže příznak povolení příkazu.|
|[COleCmdUI::SetCheck](#setcheck)|Nastaví stav přepínacího zapnuto/vypnuto příkazu.|
|[COleCmdUI::SetText](#settext)|Vrátí textový řetězec názvu nebo stavu pro příkaz.|

## <a name="remarks"></a>Poznámky

V aplikaci, která není povolená pro DocObjects, když uživatel zobrazí v nabídce v aplikaci MFC zpracovává UPDATE_COMMAND_UI generovaná. Jednotlivým oznámením je uveden [ccmdui –](../../mfc/reference/ccmdui-class.md) objekt, který lze ovládat tak, aby odrážely stavu ke konkrétnímu příkazu. Nicméně pokud vaše aplikace je povolené pro DocObjects, knihovny MFC zpracovává UPDATE_OLE_COMMAND_UI oznámení a přiřadí `COleCmdUI` objekty.

`COleCmdUI` Umožňuje DocObject přijímají příkazy, které pocházejí z příslušného kontejneru uživatelského rozhraní (například funkci FileNew, otevřít, tisk a tak dále), a kontejner pro příjem příkazy, které pocházejí z uživatelského rozhraní DocObject. I když `IDispatch` může použít k odesílání stejných příkazů `IOleCommandTarget` nabízí jednodušší způsob, jak dotazovat a provést, protože závisí na standardní sadu příkazů, obvykle bez argumentů, a je součástí žádné informace o typu. `COleCmdUI` slouží k povolení, aktualizovat a nastavit další vlastnosti DocObject uživatelských rozhraní příkazů. Pokud chcete vyvolat příkaz, volání [COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd).

Další informace o DocObjects najdete v tématu [cdocobjectserver –](../../mfc/reference/cdocobjectserver-class.md) a [cdocobjectserveritem –](../../mfc/reference/cdocobjectserveritem-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CCmdUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdocobj.h

##  <a name="colecmdui"></a>  COleCmdUI::COleCmdUI

Vytvoří `COleCmdUI` objekt přidružený k příkazu konkrétního uživatelského rozhraní.

```
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>Parametry

*rgCmds*<br/>
Seznam podporovaných příkazů, které jsou přidružené k zadaným identifikátorem GUID. `OLECMD` Struktura přidruží příkazy pomocí příznaků příkazů.

*cCmds*<br/>
Počet příkazů v *rgCmds*.

*pGroup*<br/>
Ukazatel na identifikátor GUID, který identifikuje sadu příkazů.

### <a name="remarks"></a>Poznámky

`COleCmdUI` Objekt poskytuje programové rozhraní pro aktualizace objektů uživatelského rozhraní DocObject. například položky nabídky nebo tlačítka ovládacích panelů. Objektů uživatelského rozhraní může být povolené, zakázané, zaškrtnuto nebo odbavení `COleCmdUI` objektu.

##  <a name="enable"></a>  COleCmdUI::Enable

Voláním této funkce nastavit příznak příkaz `COleCmdUI` objektu OLECOMDF_ENABLED, který informuje rozhraní příkaz je k dispozici a povolená, nebo zrušte příznak příkazu.

```
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>Parametry

*Pozvánka*<br/>
Určuje, zda příkaz přidružené `COleCmdUI` objektu by měla být povolena nebo zakázána. NonZero umožňuje příkazu; Hodnota 0 zakáže příkazu.

##  <a name="setcheck"></a>  COleCmdUI::SetCheck

Voláním této funkce pro nastavení stavu přepínač zapnuto/vypnuto příkazu.

```
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parametry

*nZkontrolujte*<br/>
Hodnota určující stav, který má nastavte přepínač zapnuto/vypnuto příkazu. Hodnoty jsou:

|Hodnota|Popis|
|-----------|-----------------|
|**1**|Příkaz nastaví na hodnotu on.|
|**2**|Nastaví příkaz do neurčitého; Stav nelze určit, protože atribut tento příkaz je v obou zapnutí a vypnutí státy v příslušné skupině.|
|jakákoli jiná hodnota|Nastavuje příkaz, který vypnuté.|

##  <a name="settext"></a>  COleCmdUI::SetText

Voláním této funkce vrátí textový řetězec názvu nebo stavu pro příkaz.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Ukazatel na text, který se použije příkaz.

## <a name="see-also"></a>Viz také:

[CCmdUI – třída](../../mfc/reference/ccmdui-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
