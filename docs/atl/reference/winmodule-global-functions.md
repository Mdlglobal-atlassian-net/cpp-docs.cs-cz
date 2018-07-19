---
title: Globální funkce WinModule | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
dev_langs:
- C++
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ac96acaf337ad3ee73f0b6f93ae6893632962e9
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884559"
---
# <a name="winmodule-global-functions"></a>Globální funkce WinModule
Tyto funkce poskytuje podporu pro `_AtlCreateWndData` struktury operace.  
  
> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
|||  
|-|-|  
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Tato funkce slouží k inicializaci a přidání `_AtlCreateWndData` struktury.|  
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Voláním této funkce extrahujete existující `_AtlCreateWndData` struktury.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  `            
##  <a name="atlwinmoduleaddcreatewnddata"></a>  AtlWinModuleAddCreateWndData  
 Tato funkce slouží k inicializaci a přidání `_AtlCreateWndData` struktury.  
   
```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```  
  
### <a name="parameters"></a>Parametry  
 *pWinModule*  
 Ukazatel na modulu [_atl_win_module70 –](../../atl/reference/atl-win-module70-structure.md) struktury.  
  
 *pData*  
 Ukazatel [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) struktura bude inicializována a přidán do aktuální modul.  
  
 *odstraněný objekt*  
 Ukazatel na objekt **to** ukazatele.  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje `_AtlCreateWndData` strukturou, který se používá k ukládání **to** ukazatel používá k odkazování na instance třídy a přidá ji do seznamu odkazuje modul `_ATL_WIN_MODULE70` struktury. Volané [CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).  
  
##  <a name="atlwinmoduleextractcreatewnddata"></a>  AtlWinModuleExtractCreateWndData  
 Voláním této funkce extrahujete existující `_AtlCreateWndData` struktury.  
 
```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```  
  
### <a name="parameters"></a>Parametry  
 *pWinModule*  
 Ukazatel na modulu [_atl_win_module70 –](../../atl/reference/atl-win-module70-structure.md) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) struktury.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce bude extrahujete existující `_AtlCreateWndData` strukturu ze seznamu odkazuje modul `_ATL_WIN_MODULE70` struktury.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../atl/reference/atl-functions.md)
