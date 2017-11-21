---
title: "Třída CDynamicChain | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
dev_langs: C++
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e66984fc7a7be45ea80dc894fcf0d11cc8febd45
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicchain-class"></a>CDynamicChain – třída
Tato třída poskytuje metody podporující dynamické řetězení mapy zpráv.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CDynamicChain
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDynamicChain::CDynamicChain](#cdynamicchain)|Konstruktor|  
|[CDynamicChain:: ~ CDynamicChain](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDynamicChain::CallChain](#callchain)|Určí, že Windows zprávu, která mapy zpráv jiný objekt.|  
|[CDynamicChain::RemoveChainEntry](#removechainentry)|Odebere položku mapování zpráv z kolekce.|  
|[CDynamicChain::SetChainEntry](#setchainentry)|Přidá položku mapování zpráv do kolekce nebo upraví existující položku.|  
  
## <a name="remarks"></a>Poznámky  
 `CDynamicChain`spravuje kolekce mapy zpráv, povolení Windows zprávu, která přesměrováni v době běhu k mapy zpráv jiný objekt.  
  
 Přidání podpory pro dynamické řetězení mapy zpráv, postupujte takto:  
  
-   Odvození třídě z `CDynamicChain`. Mapy zpráv, zadejte [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) makro ke tvoří řetěz k mapy zpráv výchozí jiný objekt.  
  
-   Odvození každá třída chcete zřetězit z [CMessageMap](../../atl/reference/cmessagemap-class.md). `CMessageMap`Umožňuje objekt vystavit jeho mapy zpráv na jiné objekty.  
  
-   Volání `CDynamicChain::SetChainEntry` k identifikaci, který objekt a mapování zpráv, které chcete řetězce pro.  
  
 Předpokládejme například, že třídě je definován následujícím způsobem:  
  
 [!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]  
  
 Klient pak zavolá `CMyWindow::SetChainEntry`:  
  
 [!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]  
  
 kde `chainedObj` je objekt zřetězené a je instance třídy odvozené od `CMessageMap`. Nyní pokud `myCtl` obdrží zprávu, která není zpracováván `OnPaint` nebo `OnSetFocus`, postup okno přesměruje zprávu, která se `chainedObj`na výchozí mapy zpráv.  
  
 Další informace o řetězení mapy zpráv najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md) v článku "Tříd oken ATL."  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="callchain"></a>CDynamicChain::CallChain  
 Určí, že Windows zprávu, která se mapy zpráv jiný objekt.  
  
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
 `dwChainID`  
 [v] Jedinečný identifikátor přidružený objekt zřetězené a jeho mapy zpráv.  
  
 `hWnd`  
 [v] Popisovač okna danou zprávu přijala.  
  
 `uMsg`  
 [v] Zpráva odeslaná do okna.  
  
 `wParam`  
 [v] Další informace specifické pro zprávy.  
  
 `lParam`  
 [v] Další informace specifické pro zprávy.  
  
 `lResult`  
 [out] Výsledek zpracování zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud zpráva je plně zpracovaná; v opačném **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Okno postup vyvolání `CallChain`, je nutné zadat [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) makro mapy zpráv. Příklad, naleznete v části [CDynamicChain](../../atl/reference/cdynamicchain-class.md) Přehled.  
  
 `CallChain`vyžaduje předchozí volání [SetChainEntry](#setchainentry) přidružit `dwChainID` hodnotu s objektu a jeho mapy zpráv.  
  
##  <a name="cdynamicchain"></a>CDynamicChain::CDynamicChain  
 Konstruktor  
  
```
CDynamicChain();
```  
  
##  <a name="dtor"></a>CDynamicChain:: ~ CDynamicChain  
 Destruktor.  
  
```
~CDynamicChain();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
##  <a name="removechainentry"></a>CDynamicChain::RemoveChainEntry  
 Odebere určenou zprávu mapy z kolekce.  
  
```
BOOL RemoveChainEntry(DWORD dwChainID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwChainID`  
 [v] Jedinečný identifikátor přidružený objekt zřetězené a jeho mapy zpráv. Původně definovat tuto hodnotu prostřednictvím volání [SetChainEntry](#setchainentry).  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud mapy zpráv se úspěšně odebral z kolekce. V opačném **FALSE**.  
  
##  <a name="setchainentry"></a>CDynamicChain::SetChainEntry  
 Přidá určenou zprávu mapy do kolekce.  
  
```
BOOL SetChainEntry(  
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `dwChainID`  
 [v] Jedinečný identifikátor přidružený objekt zřetězené a jeho mapy zpráv.  
  
 `pObject`  
 [v] Ukazatel na objekt zřetězené deklarace mapy zpráv. Tento objekt musí být odvozeny od [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
 `dwMsgMapID`  
 [v] Identifikátor mapy zpráv v zřetězené objektu. Výchozí hodnota je 0, který identifikuje výchozí mapování zpráv deklarovat s [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). K určení mapování alternativní zpráva deklarovat s [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), předat `msgMapID`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud mapy zpráv se úspěšně přidal do kolekce. V opačném **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `dwChainID` hodnota již existuje v kolekci, jeho přidružený objekt a mapy zpráv se nahrazují `pObject` a `dwMsgMapID`, v uvedeném pořadí. Jinak je přidat novou položku.  
  
## <a name="see-also"></a>Viz také  
 [CWindowImpl – třída](../../atl/reference/cwindowimpl-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
