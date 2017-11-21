---
title: "Globální funkce COM mapy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
dev_langs: C++
helpviewer_keywords: COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8a5c73f99d8d31ad500b232d371bf55072dd567a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="com-map-global-functions"></a>Globální funkce mapu modelu COM
Tyto funkce poskytuje podporu pro mapu modelu COM **IUnknown** implementace.  
  
|||  
|-|-|  
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Deleguje **IUnknown** neagregovaná objektu.|  
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Generuje efektivní kód pro porovnání rozhraní proti **IUnknown**.|  

  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  

##  <a name="atlinternalqueryinterface"></a>AtlInternalQueryInterface  
 Načte ukazatel na požadované rozhraní.  
  
```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `pThis`  
 [v] Ukazatel na objekt, který obsahuje mapy COM rozhraní vystavený `QueryInterface`.  
  
 `pEntries`  
 [v] Pole **_ATL_INTMAP_ENTRY** struktury, které mapě k dispozici rozhraní.  
  
 `iid`  
 [v] Identifikátor GUID se požadované rozhraní.  
  
 `ppvObject`  
 [out] Ukazatel na ukazatel rozhraní zadaný v `iid`, nebo **NULL** Pokud rozhraní nebyl nalezen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 `AtlInternalQueryInterface`zpracovává jenom rozhraní v tabulce COM mapy. Pokud je agregován objektu, `AtlInternalQueryInterface` není delegovat na vnější neznámý. Rozhraní můžete zadat do tabulky mapování COM s makro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) nebo jednoho z jeho variant.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]  
  
##  <a name="inlineisequaliunknown"></a>InlineIsEqualIUnknown  
 Volání této funkce pro zvláštní případ testování pro **IUnknown**.  
  
```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```  
  
### <a name="parameters"></a>Parametry  
 *rguid1*  
 [v] Identifikátor GUID, který má být porovnán **IID_IUnknown**.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../atl/reference/atl-functions.md)   
 [Makra COM Map](../../atl/reference/com-map-macros.md)
