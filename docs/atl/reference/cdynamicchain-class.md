---
title: Třída CDynamicChain
ms.date: 11/04/2016
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
ms.openlocfilehash: 4a72b3b4308ed83dfdc4a2895a04d1fe9a177ce5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327037"
---
# <a name="cdynamicchain-class"></a>Třída CDynamicChain

Tato třída poskytuje metody podporující dynamické zřetězení map zpráv.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CDynamicChain
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CDynamicChain::CDynamicChain](#cdynamicchain)|Konstruktor|
|[CDynamicChain::~CDynamicChain](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDynamicChain::CallChain](#callchain)|Přesměruje zprávu systému Windows na mapu zpráv jiného objektu.|
|[CDynamicChain::RemoveChainEntry](#removechainentry)|Odebere položku mapy zpráv z kolekce.|
|[CDynamicChain::SetChainEntry](#setchainentry)|Přidá položku mapy zpráv do kolekce nebo upraví existující položku.|

## <a name="remarks"></a>Poznámky

`CDynamicChain`spravuje kolekci map zpráv, která umožňuje, aby zpráva systému Windows byla za běhu přesměrována na mapu zpráv jiného objektu.

Chcete-li přidat podporu dynamického řetězení map zpráv, postupujte takto:

- Odvodit `CDynamicChain`třídu z . V mapě zpráv určete [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) makro, které má být zřetězeno na výchozí mapu zpráv jiného objektu.

- Odvodit každou třídu, kterou chcete zřetězit z [CMessageMap](../../atl/reference/cmessagemap-class.md). `CMessageMap`umožňuje objektu vystavit jeho mapy zpráv na jiné objekty.

- Volání `CDynamicChain::SetChainEntry` k identifikaci objektu a mapy zprávy, ke které chcete zřetězit.

Předpokládejme například, že vaše třída je definována takto:

[!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]

Klient pak `CMyWindow::SetChainEntry`volá :

[!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]

kde `chainedObj` je zřetězený objekt a je instancí třídy odvozené z `CMessageMap`. Nyní, `myCtl` pokud obdrží zprávu, která `OnPaint` není `OnSetFocus`zpracována nebo , procedura okna přesměruje zprávu na `chainedObj`výchozí mapu zpráv .

Další informace o řetězení mapy zpráv naleznete v tématu [Mapy zpráv](../../atl/message-maps-atl.md) v článku "Třídy oken ATL.".

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="cdynamicchaincallchain"></a><a name="callchain"></a>CDynamicChain::CallChain

Přesměruje zprávu systému Windows na mapu zpráv jiného objektu.

```
BOOL CallChain(
    DWORD dwChainID,
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult);
```

### <a name="parameters"></a>Parametry

*dwChainID*<br/>
[v] Jedinečný identifikátor přidružený k zřetězený objekt a jeho mapy zpráv.

*Hwnd*<br/>
[v] Popisovač do okna, které přijímá zprávu.

*uMsg*<br/>
[v] Zpráva odeslaná do okna.

*wParam*<br/>
[v] Další informace specifické pro zprávu.

*Lparam*<br/>
[v] Další informace specifické pro zprávu.

*lVýsledek*<br/>
[out] Výsledek zpracování zprávy.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je zpráva plně zpracována; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Chcete-li vyvolat `CallChain`proceduru okna , je nutné zadat [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) makro v mapě zpráv. Například viz přehled [CDynamicChain.](../../atl/reference/cdynamicchain-class.md)

`CallChain`vyžaduje předchozí volání [SetChainEntry](#setchainentry) přidružit hodnotu *dwChainID* k objektu a jeho mapování zpráv.

## <a name="cdynamicchaincdynamicchain"></a><a name="cdynamicchain"></a>CDynamicChain::CDynamicChain

Konstruktor

```
CDynamicChain();
```

## <a name="cdynamicchaincdynamicchain"></a><a name="dtor"></a>CDynamicChain::~CDynamicChain

Destruktor.

```
~CDynamicChain();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje.

## <a name="cdynamicchainremovechainentry"></a><a name="removechainentry"></a>CDynamicChain::RemoveChainEntry

Odebere zadanou mapu zpráv z kolekce.

```
BOOL RemoveChainEntry(DWORD dwChainID);
```

### <a name="parameters"></a>Parametry

*dwChainID*<br/>
[v] Jedinečný identifikátor přidružený k zřetězený objekt a jeho mapy zpráv. Tuto hodnotu původně definujete voláním [SetChainEntry](#setchainentry).

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je mapa zpráv úspěšně odebrána z kolekce. V opačném případě NEPRAVDA.

## <a name="cdynamicchainsetchainentry"></a><a name="setchainentry"></a>CDynamicChain::SetChainEntry

Přidá zadanou mapu zpráv do kolekce.

```
BOOL SetChainEntry(
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```

### <a name="parameters"></a>Parametry

*dwChainID*<br/>
[v] Jedinečný identifikátor přidružený k zřetězený objekt a jeho mapy zpráv.

*pObjekt*<br/>
[v] Ukazatel na zřetězený objekt deklarující mapu zpráv. Tento objekt musí být odvozen z [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[v] Identifikátor mapy zpráv v zřetězený objekt. Výchozí hodnota je 0, která identifikuje výchozí mapu zpráv deklarovanou [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Chcete-li určit alternativní mapu zpráv deklarovanou pomocí `msgMapID` [ALT_MSG_MAP(msgMapID),](message-map-macros-atl.md#alt_msg_map)předaj .

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je mapa zpráv úspěšně přidána do kolekce. V opačném případě NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pokud hodnota *dwChainID* již v kolekci existuje, její přidružené mapování objektu a zpráv jsou nahrazeny *pObject* a *dwMsgMapID*. V opačném případě je přidána nová položka.

## <a name="see-also"></a>Viz také

[Třída CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
