---
title: Makra COM Map | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74f8903d81a126a6647bc43018f8422296ddf970
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358420"
---
# <a name="com-map-macros"></a>Makra COM Map
Tyto makra definovat COM rozhraní mapy.  
  
|||  
|-|-|  
|[BEGIN_COM_MAP](#begin_com_map)|Označuje začátek položek mapování rozhraní COM.|  
|[END_COM_MAP](#end_com_map)|Označuje konec položek mapování rozhraní COM.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
   
##  <a name="begin_com_map"></a>  BEGIN_COM_MAP  
 Mapa COM je mechanismus, který zveřejňuje rozhraní objektu klientovi prostřednictvím `QueryInterface`.  
  
```
BEGIN_COM_MAP(x)
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [v] Název objektu třídy jsou zpřístupňuje rozhraní na.  
  
### <a name="remarks"></a>Poznámky  
 [CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) vrátí pouze ukazatele pro rozhraní COM mapy. Spuštění mapy rozhraní s `BEGIN_COM_MAP` makro, přidejte položky pro každý z vašich rozhraní s [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) makro nebo jednoho z jeho variant a dokončete mapa s [END_COM_MAP](#end_com_map) makro.  

  
### <a name="example"></a>Příklad  
 Z knihovny ATL [BEEPER](../../visual-cpp-samples.md) ukázka:  
  
 [!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  

  
##  <a name="end_com_map"></a>  END_COM_MAP  
 Ukončí definici mapy rozhraní modelu COM.  
  
```
END_COM_MAP()
```  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)   
 [Globální funkce mapy modelu COM](../../atl/reference/com-map-global-functions.md)
