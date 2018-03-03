---
title: "Globální funkce registrace serveru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
dev_langs:
- C++
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f5cfffbcc47555ee8cff7cd6e18ea54b5524607
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="server-registration-global-functions"></a>Globální funkce registrace serveru
Tyto funkce poskytuje podporu pro registraci a zrušení registrace serveru objekty v mapování objektu.  
  
> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze používat v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
|||  
|-|-|  
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|Voláním této funkce se zaregistrují všechny objekty v mapě objektů.|  
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|Voláním této funkce se zruší registrace všech objektů v mapě objektů.|  
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|Voláním této funkce se zaregistrují objekty třídy.|  
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|Tato funkce je volána k odvolání objekty tříd z modulu COM.|  
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|Tato funkce je volána potřebujete objektu třídy.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
   
##  <a name="atlcommoduleregisterserver"></a>AtlComModuleRegisterServer  
 Voláním této funkce se zaregistrují všechny objekty v mapě objektů.  
  
```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```  
  
### <a name="parameters"></a>Parametry  
 `pComModule`  
 Ukazatel na modulu COM.  
  
 `bRegTypeLib`  
 TRUE, pokud je typ knihovna k registraci.  
  
 `pCLSID`  
 Body CLSID objekt, který má být zaregistrován. Pokud hodnotu NULL, se zaregistruje všechny objekty v mapování objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 `AtlComModuleRegisterServer`provede mapování objektu generován automaticky ATL a zaregistruje každý objekt v mapě. Pokud `pCLSID` není NULL a pouze objekty, na kterou odkazuje `pCLSID` je zaregistrován; v opačném případě všechny objekty jsou registrované.  
  
 Tato funkce je volána [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver).  
  
##  <a name="atlcommoduleunregisterserver"></a>AtlComModuleUnregisterServer  
 Voláním této funkce se zruší registrace všech objektů v mapě objektů.  
  
```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```  
  
### <a name="parameters"></a>Parametry  
 `pComModule`  
 Ukazatel na modulu COM.  
  
 `bUnRegTypeLib`  
 TRUE, pokud je typ knihovna k registraci.  
  
 `pCLSID`  
 Body CLSID objekt, který má neregistrované. Pokud hodnotu NULL. všechny objekty v mapování objektu bude zrušena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 `AtlComModuleUnregisterServer`provede mapování objektu knihovny ATL a zrušení registrace každý objekt v mapě. Pokud `pCLSID` není NULL a pouze objekty, na kterou odkazuje `pCLSID` registrace; jinak hodnota všechny objekty se zrušit registraci.  
  
 Tato funkce je volána [CAtlComModule::UnregisterServer](catlcommodule-class.md#unregisterserver).  
  
##  <a name="atlcommoduleregisterclassobjects"></a>AtlComModuleRegisterClassObjects  
 Voláním této funkce se zaregistrují objekty třídy.  
  
```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `pComModule`  
 Ukazatel na modulu COM.  
  
 `dwClsContext`  
 Určuje kontext, ve kterém má být spuštěna objektu třídy. Možné hodnoty jsou CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER nebo CLSCTX_LOCAL_SERVER. V tématu [CLSCTX](http://msdn.microsoft.com/library/windows/desktop/ms693716) další podrobnosti.  
  
 `dwFlags`  
 Určuje typy připojení k objektu třídy. Možné hodnoty jsou REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE nebo REGCLS_MULTI_SEPARATE. V tématu [REGCLS](http://msdn.microsoft.com/library/windows/desktop/ms679697) další podrobnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato pomocná funkce je využíváno [CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) (v ATL 7.0 zastaralé) a [CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects).  
  
##  <a name="atlcommodulerevokeclassobjects"></a>AtlComModuleRevokeClassObjects  
 Voláním této funkce se z tabulky spuštěných objektů odeberou objekty pro vytváření tříd.  
  
```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```  
  
### <a name="parameters"></a>Parametry  
 `pComModule`  
 Ukazatel na modulu COM.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato pomocná funkce je využíváno [CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (v ATL 7.0 zastaralé) a [CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects).  
  
##  <a name="atlcommodulegetclassobject"></a>AtlComModuleGetClassObject  
 Voláním této funkce se vrátí objekt pro vytváření tříd.  
  
```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```  
  
### <a name="parameters"></a>Parametry  
 `pComModule`  
 Ukazatel na modulu COM.  
  
 `rclsid`  
 CLSID objektu, který se má vytvořit.  
  
 `riid`  
 Identifikátory IID požadované rozhraní.  
  
 `ppv`  
 Ukazatel na ukazatel rozhraní identifikovaný `riid`. Pokud objekt nepodporuje toto rozhraní `ppv` je nastaven na hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato pomocná funkce je využíváno [CComModule::GetClassObject](ccommodule-class.md#getclassobject) (v ATL 7.0 zastaralé) a [CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject).  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../atl/reference/atl-functions.md)
