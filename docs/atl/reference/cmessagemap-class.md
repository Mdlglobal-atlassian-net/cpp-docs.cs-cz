---
title: Cmessagemap – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae6f41c2e8e8d142ee143d7ba0829751e1c230a3
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465659"
---
# <a name="cmessagemap-class"></a>Cmessagemap – třída
Tato třída umožňuje že mapy zpráv objektu bude přístup k jiným objektem.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class ATL_NO_VTABLE CMessageMap
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|Přistupuje k mapy zpráv v `CMessageMap`-odvozené třídy.|  
  
## <a name="remarks"></a>Poznámky  
 `CMessageMap` je abstraktní základní třídu, která umožňuje zpráva objektu se mapuje na přístupná pomocí jiného objektu. Aby objekt vystavit jeho mapy zpráv, její třída musí být odvozen od `CMessageMap`.  
  
 ATL – používá `CMessageMap` obsahovala podporu windows a dynamických zpráv řetězení mapy. Například všechny třídy obsahující [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) objekt musí být odvozen od `CMessageMap`. Následující kód je převzatý z [SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) vzorku. Prostřednictvím [ccomcontrol –](../../atl/reference/ccomcontrol-class.md), `CAtlEdit` třídy je automaticky odvozen z `CMessageMap`.  
  
 [!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]  
  
 Protože obsaženého okna `m_EditCtrl`, použije mapy zpráv ve třídě obsahující `CAtlEdit` je odvozena z `CMessageMap`.  
  
 Další informace o mapách zpráv najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md) v článku "Tříd oken ATL."  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="processwindowmessage"></a>  CMessageMap::ProcessWindowMessage  
 Přistupuje k mapu zpráv identifikovaný *dwMsgMapID* v `CMessageMap`-odvozené třídy.  
  
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
  
 *dwMsgMapID*  
 [in] Identifikátor, který bude zpracovávat zprávy mapování zprávy. Výchozí zprávu mapování deklarována s [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), je identifikován 0. Mapování zpráv alternativní deklarované s [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), je identifikován `msgMapID`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud zpráva je plně zpracovány; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Volané procedury okna nástroje [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) objektu nebo objektu, která je dynamicky řetězení v mapování zprávy.  
  
## <a name="see-also"></a>Viz také  
 [Cdynamicchain – třída](../../atl/reference/cdynamicchain-class.md)   
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)   
 [Přehled tříd](../../atl/atl-class-overview.md)
