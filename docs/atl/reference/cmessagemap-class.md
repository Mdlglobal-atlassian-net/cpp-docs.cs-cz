---
title: "Třída CMessageMap | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
dev_langs:
- C++
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 04aff6922358048fcbd330096eb26a412cdb75ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmessagemap-class"></a>CMessageMap – třída
Tato třída umožňuje že mapy zpráv objektu být přístup k jinému objektu.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class ATL_NO_VTABLE CMessageMap
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|Mapy zpráv v přistupuje `CMessageMap`-odvozené třídy.|  
  
## <a name="remarks"></a>Poznámky  
 `CMessageMap`je abstraktní základní třída, která umožňuje objektu zpráva mapuje přístup k jinému objektu. Aby objekt vystavit jeho mapy zpráv, její třída musí být odvozeny od `CMessageMap`.  
  
 ATL používá `CMessageMap` podporu obsažené windows a dynamické zpráva řetězení mapy. Například všechny třída obsahující [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) objekt musí být odvozeny od `CMessageMap`. Následující kód je převzat ze [SUBEDIT](../../visual-cpp-samples.md) ukázka. Prostřednictvím [CComControl](../../atl/reference/ccomcontrol-class.md), `CAtlEdit` třída automaticky odvozena z `CMessageMap`.  
  
 [!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]  
  
 Protože okno obsažené `m_EditCtrl`, použije mapy zpráv ve třídě obsahující `CAtlEdit` je odvozena z `CMessageMap`.  
  
 Další informace o mapách zpráv najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md) v článku "Tříd oken ATL."  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="processwindowmessage"></a>CMessageMap::ProcessWindowMessage  
 Mapy zpráv identifikovaný přistupuje k `dwMsgMapID` v `CMessageMap`-odvozené třídy.  
  
```
virtual BOOL ProcessWindowMessage(  
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult,
    DWORD dwMsgMapID) = 0;
```  
  
### <a name="parameters"></a>Parametry  
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
  
 `dwMsgMapID`  
 [v] Identifikátor mapy zpráv, která zpracuje zprávu. Mapa zpráv výchozí deklarovat s [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), je identifikovaný 0. Mapování zpráv alternativní deklarovat s [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), je identifikovaný `msgMapID`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud zpráva je plně zpracovávaný; v opačném **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Volá proceduru okna nástroje [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) objektu nebo objektu, se dynamicky řetězení do mapy zpráv.  
  
## <a name="see-also"></a>Viz také  
 [CDynamicChain – třída](../../atl/reference/cdynamicchain-class.md)   
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)   
 [Přehled třídy](../../atl/atl-class-overview.md)
