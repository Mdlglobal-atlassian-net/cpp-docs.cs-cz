---
title: Makra bodů připojení | Dokumentace Microsoftu
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
ms.openlocfilehash: 88789bef4bbcce3df99d90d736974377c9bca5fd
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882933"
---
# <a name="connection-point-macros"></a>Makra bodů připojení
Tato makra definují připojení bodu mapy a položky.  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Označuje začátek položek mapování bodu připojení.|  
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Zadá spojovacích bodů do objektu map.|  
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) Podobně jako CONNECTION_POINT_ENTRY ale bere ukazatel na iid.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Označuje konec položek mapování bodu připojení.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom 
   
##  <a name="begin_connection_point_map"></a>  BEGIN_CONNECTION_POINT_MAP  
 Označuje začátek položek mapování bodu připojení.  
  
```
BEGIN_CONNECTION_POINT_MAP(x)
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Název třídy, který obsahuje spojovací body.  
  
### <a name="remarks"></a>Poznámky  
 Začínat – makro BEGIN_CONNECTION_POINT_MAP připojení bodu mapy, přidejte položky pro každý z vašich spojovací body s [CONNECTION_POINT_ENTRY](#connection_point_entry) – makro a proveďte mapování [END_CONNECTION_ POINT_MAP](#end_connection_point_map) – makro.  
  
 Další informace o spojovacích bodů ve ATL naleznete v článku [spojovací body](../../atl/atl-connection-points.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]  
  
##  <a name="connection_point_entry"></a>  CONNECTION_POINT_ENTRY a CONNECTION_POINT_ENTRY_P  
 Zadá bodu připojení pro zadané rozhraní do objektu map bodu připojení tak, aby byla přístupná.  
  
```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parametry  
 *identifikátor IID*  
 [in] Identifikátor GUID rozhraní se přidávají do mapy bodu připojení. 
 
 *piid*  
 [in] Ukazatel na identifikátor GUID rozhraní se adde.   
  
### <a name="remarks"></a>Poznámky  
 Připojení bodu položky na mapě jsou používány [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md). Třída obsahující mapě bod připojení musí dědit z `IConnectionPointContainerImpl`.  
  
 Spuštění mapy bod připojení se [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) – makro, přidejte položky pro každý z vašich spojovací body s – makro CONNECTION_POINT_ENTRY a dokončení mapování se [END_CONNECTION_ POINT_MAP](#end_connection_point_map) – makro.  
  
 Další informace o spojovacích bodů ve ATL naleznete v článku [spojovací body](../../atl/atl-connection-points.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]  
  
##  <a name="end_connection_point_map"></a>  END_CONNECTION_POINT_MAP  
 Označuje konec položek mapování bodu připojení.  
  
```
END_CONNECTION_POINT_MAP()
```  
  
### <a name="remarks"></a>Poznámky  
 Spuštění mapy bod připojení se [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) – makro, přidejte položky pro každý z vašich spojovací body s [CONNECTION_POINT_ENTRY](#connection_point_entry) – makro a proveďte mapování END_ CONNECTION_POINT_MAP makra.  
  
 Další informace o spojovacích bodů ve ATL naleznete v článku [spojovací body](../../atl/atl-connection-points.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)   
 [Globální funkce bodů připojení](../../atl/reference/connection-point-global-functions.md)
