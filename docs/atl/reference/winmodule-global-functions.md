---
title: "Globální funkce WinModule | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
dev_langs: C++
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5435b9870a396f24cb2aca5889c9fcfbc90d879a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="winmodule-global-functions"></a>Globální funkce WinModule
Tyto funkce poskytuje podporu pro `_AtlCreateWndData` struktury operace.  
  
> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze používat v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
|||  
|-|-|  
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Tato funkce slouží k inicializaci a přidejte `_AtlCreateWndData` struktura.|  
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Volání této funkce k extrakci existující `_AtlCreateWndData` struktura.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  `            
##  <a name="atlwinmoduleaddcreatewnddata"></a>AtlWinModuleAddCreateWndData  
 Tato funkce slouží k inicializaci a přidejte `_AtlCreateWndData` struktura.  
   
```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```  
  
### <a name="parameters"></a>Parametry  
 `pWinModule`  
 Ukazatel na modul [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) struktury.  
  
 `pData`  
 Ukazatel [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) struktura inicializovat a přidat je do aktuální modulu.  
  
 `pObject`  
 Ukazatele na objekt **to** ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje `_AtlCreateWndData` strukturu, která se používá k ukládání **to** ukazatel označují instancí tříd a přidá ji do seznamu odkazuje modul `_ATL_WIN_MODULE70` struktura. Voláno rozhraním [CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).  
  
##  <a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModuleExtractCreateWndData  
 Volání této funkce k extrakci existující `_AtlCreateWndData` struktura.  
 
```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```  
  
### <a name="parameters"></a>Parametry  
 `pWinModule`  
 Ukazatel na modul [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) struktury.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce bude extrahovat existující `_AtlCreateWndData` struktura ze seznamu odkazuje modul `_ATL_WIN_MODULE70` struktura.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../atl/reference/atl-functions.md)
