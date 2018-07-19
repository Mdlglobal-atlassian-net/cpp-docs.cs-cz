---
title: Cdynamicchain – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
dev_langs:
- C++
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a279dac7e2a9f4e58954ac6637eaf2b56ad801b2
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884139"
---
# <a name="cdynamicchain-class"></a>Cdynamicchain – třída
Tato třída poskytuje metody, které podporuje dynamické řetězení mapy zpráv.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CDynamicChain
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDynamicChain::CDynamicChain](#cdynamicchain)|Konstruktor|  
|[Cdynamicchain –:: ~ cdynamicchain –](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDynamicChain::CallChain](#callchain)|Přesměruje zpráv Windows do mapy zpráv jiného objektu.|  
|[CDynamicChain::RemoveChainEntry](#removechainentry)|Odebere položku mapování zpráv z kolekce.|  
|[CDynamicChain::SetChainEntry](#setchainentry)|Přidá položku mapování zpráv do kolekce nebo upraví existující položka.|  
  
## <a name="remarks"></a>Poznámky  
 `CDynamicChain` Spravuje kolekci mapy zpráv, povolení zprávu Windows přejdete v době běhu na jiný objekt mapování zprávy.  
  
 Přidání podpory pro dynamické řetězení mapy zpráv, postupujte takto:  
  
-   Odvodit třídu z `CDynamicChain`. V mapování zprávy, zadejte [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) – makro do řetězce do jiného objektu výchozí zprávu mapy.  
  
-   Jsou odvozeny všechny třídy, které chcete zřetězit z [cmessagemap –](../../atl/reference/cmessagemap-class.md). `CMessageMap` Umožňuje zobrazit jeho mapy zpráv na jiné objekty.  
  
-   Volání `CDynamicChain::SetChainEntry` tím určíte, které objekt a mapování zpráv, které chcete ke sledu k.  
  
 Předpokládejme například, že vaše třída je definována takto:  
  
 [!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]  
  
 Klient pak zavolá `CMyWindow::SetChainEntry`:  
  
 [!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]  
  
 kde `chainedObj` zřetězené objekt a instance třídy odvozené od `CMessageMap`. Nyní pokud `myCtl` obdrží zprávu, která není zpracována `OnPaint` nebo `OnSetFocus`, přesměruje zpráva, kterou chcete proceduru okna `chainedObj`na výchozí mapování zprávy.  
  
 Další informace o řetězení mapy zpráv, najdete v části [mapy zpráv](../../atl/message-maps-atl.md) v článku "Tříd oken ATL."  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="callchain"></a>  CDynamicChain::CallChain  
 Přesměruje Windows zpráva, která má jiný objekt mapování zprávy.  
  
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
 *dwChainID*  
 [in] Jedinečný identifikátor přidružený k zřetězené objektu a jeho mapování zprávy.  
  
 *hWnd*  
 [in] Popisovač okna příjem zprávy.  
  
 *uMsg*  
 [in] Zpráva odeslaná do okna.  
  
 *wParam*  
 [in] Další informace specifické pro zprávy.  
  
 *lParam*  
 [in] Další informace specifické pro zprávy.  
  
 *lResult*  
 [out] Výsledek zpracování zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud zprávy budou plně zpracovány; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Pro proceduru okna, který má být vyvolán `CallChain`, je nutné zadat [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) – makro v mapě zpráv. Příklad najdete v tématu [cdynamicchain –](../../atl/reference/cdynamicchain-class.md) Přehled.  
  
 `CallChain` vyžaduje, aby předchozí volání [SetChainEntry](#setchainentry) přidružení *dwChainID* hodnotu objektu a jeho mapování zprávy.  
  
##  <a name="cdynamicchain"></a>  CDynamicChain::CDynamicChain  
 Konstruktor  
  
```
CDynamicChain();
```  
  
##  <a name="dtor"></a>  Cdynamicchain –:: ~ cdynamicchain –  
 Destruktor.  
  
```
~CDynamicChain();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
##  <a name="removechainentry"></a>  CDynamicChain::RemoveChainEntry  
 Mapa zadaná zpráva odebere z kolekce.  
  
```
BOOL RemoveChainEntry(DWORD dwChainID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwChainID*  
 [in] Jedinečný identifikátor přidružený k zřetězené objektu a jeho mapování zprávy. Původně definovat tuto hodnotu přímo pomocí volání [SetChainEntry](#setchainentry).  
  
### <a name="return-value"></a>Návratová hodnota  
 TRUE, pokud mapu zpráv se úspěšně odebral z kolekce. V opačném případě hodnota FALSE.  
  
##  <a name="setchainentry"></a>  CDynamicChain::SetChainEntry  
 Přidá mapování určenou zprávu do kolekce.  
  
```
BOOL SetChainEntry(  
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *dwChainID*  
 [in] Jedinečný identifikátor přidružený k zřetězené objektu a jeho mapování zprávy.  
  
 *odstraněný objekt*  
 [in] Ukazatel na objekt zřetězené deklarace mapování zprávy. Tento objekt musí být odvozen od [cmessagemap –](../../atl/reference/cmessagemap-class.md).  
  
 *dwMsgMapID*  
 [in] Identifikátor mapu zpráv ve zřetězených objektů. Výchozí hodnota je 0, což označuje výchozí mapování zpráv deklarována s [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Chcete-li určit mapování alternativních zpráva deklarována s [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), předejte `msgMapID`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud mapu zpráv je úspěšně přidaný do kolekce. V opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *dwChainID* hodnota již existuje v kolekci, jeho přidruženého objektu a mapování zpráv se nahrazují *odstraněný objekt* a *dwMsgMapID*v uvedeném pořadí. V opačném případě se přidá nová položka.  
  
## <a name="see-also"></a>Viz také  
 [Cwindowimpl – třída](../../atl/reference/cwindowimpl-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
