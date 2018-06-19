---
title: Globální funkce COM mapy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 509479a923203acd80eaac1ef90aa64125d208c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359876"
---
# <a name="com-map-global-functions"></a>Globální funkce mapu modelu COM
Tyto funkce poskytuje podporu pro mapu modelu COM **IUnknown** implementace.  
  
|||  
|-|-|  
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Deleguje **IUnknown** neagregovaná objektu.|  
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Generuje efektivní kód pro porovnání rozhraní proti **IUnknown**.|  

  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  

##  <a name="atlinternalqueryinterface"></a>  AtlInternalQueryInterface  
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
 `AtlInternalQueryInterface` Zpracovává jenom rozhraní v tabulce COM mapy. Pokud je agregován objektu, `AtlInternalQueryInterface` není delegovat na vnější neznámý. Rozhraní můžete zadat do tabulky mapování COM s makro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) nebo jednoho z jeho variant.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]  
  
##  <a name="inlineisequaliunknown"></a>  InlineIsEqualIUnknown  
 Volání této funkce pro zvláštní případ testování pro **IUnknown**.  
  
```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```  
  
### <a name="parameters"></a>Parametry  
 *rguid1*  
 [v] Identifikátor GUID, který má být porovnán **IID_IUnknown**.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../atl/reference/atl-functions.md)   
 [Makra map COM](../../atl/reference/com-map-macros.md)
