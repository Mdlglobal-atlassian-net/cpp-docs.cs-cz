---
title: Makra bodu připojení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e50a868dd87628873b2a43f0ace55690b0583fd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="connection-point-macros"></a>Makra bodu připojení
Tyto makra definovat mapy bodu připojení a položky.  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Označuje začátek položek mapování bod připojení.|  
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Body připojení vstoupí do mapy.|  
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) Podobá se CONNECTION_POINT_ENTRY ale má ukazatel na iid.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Označuje konec položek mapování bod připojení.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom 
   
##  <a name="begin_connection_point_map"></a>  BEGIN_CONNECTION_POINT_MAP  
 Označuje začátek položek mapování bod připojení.  
  
```
BEGIN_CONNECTION_POINT_MAP(x)
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [v] Název třídy obsahující spojovací body.  
  
### <a name="remarks"></a>Poznámky  
 Spuštění mapy bodu připojení s `BEGIN_CONNECTION_POINT_MAP` makro, přidejte položky pro všechny body připojení [CONNECTION_POINT_ENTRY](#connection_point_entry) makro a dokončete mapa s [END_CONNECTION_POINT_MAP](#end_connection_point_map) makro.  
  
 Další informace o bodech připojení v ATL, najdete v článku [spojovací body](../../atl/atl-connection-points.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]  
  
##  <a name="connection_point_entry"></a>  CONNECTION_POINT_ENTRY a CONNECTION_POINT_ENTRY_P  
 Zadá bod připojení pro rozhraní zadané do bodu mapy připojení tak, aby k němu.  
  
```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Identifikátor GUID rozhraní, který se přidává do bodu mapy připojení. 
 
 `piid`  
 [v] Ukazatel na identifikátor GUID rozhraní se adde.   
  
### <a name="remarks"></a>Poznámky  
 Připojení bodu položky v mapě používá [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md). Třída obsahující bodu mapy připojení musí dědit z `IConnectionPointContainerImpl`.  
  
 Spuštění mapy bodu připojení s [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) makro, přidejte položky pro všechny body připojení `CONNECTION_POINT_ENTRY` makro a dokončete mapa s [END_CONNECTION_POINT_MAP ](#end_connection_point_map) makro.  
  
 Další informace o bodech připojení v ATL, najdete v článku [spojovací body](../../atl/atl-connection-points.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]  
  
##  <a name="end_connection_point_map"></a>  END_CONNECTION_POINT_MAP  
 Označuje konec položek mapování bod připojení.  
  
```
END_CONNECTION_POINT_MAP()
```  
  
### <a name="remarks"></a>Poznámky  
 Spuštění mapy bodu připojení s [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) makro, přidejte položky pro všechny body připojení [CONNECTION_POINT_ENTRY](#connection_point_entry) makro a dokončete mapa s `END_CONNECTION_POINT_MAP` makro.  
  
 Další informace o bodech připojení v ATL, najdete v článku [spojovací body](../../atl/atl-connection-points.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)   
 [Globální funkce bodů připojení](../../atl/reference/connection-point-global-functions.md)
