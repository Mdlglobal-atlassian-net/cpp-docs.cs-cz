---
title: Globální funkce serverové registrace
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
ms.openlocfilehash: f97a4ff0dc28077d42fe0f8ca4992946db4082f1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441786"
---
# <a name="server-registration-global-functions"></a>Globální funkce serverové registrace

Tyto funkce poskytují podporu registrace a zrušení registrace serveru objekty v mapě objektů.

> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

|||
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|Voláním této funkce se zaregistrují všechny objekty v mapě objektů.|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|Voláním této funkce se zruší registrace všech objektů v mapě objektů.|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|Voláním této funkce se zaregistrují objekty třídy.|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|Tato funkce je volána k odvolání objekty třídy z modulu COM.|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|Tato funkce je volána k získání objektu třídy.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="atlcommoduleregisterserver"></a>  AtlComModuleRegisterServer

Voláním této funkce se zaregistrují všechny objekty v mapě objektů.

```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>Parametry

*pComModule*<br/>
Ukazatel na modulu COM.

*bRegTypeLib*<br/>
TRUE, pokud knihovna typů je k registraci.

*pCLSID*<br/>
Odkazuje na identifikátor CLSID objekt, který má být zaregistrován. Pokud má hodnotu NULL, se zaregistruje všechny objekty v mapě objektů.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

`AtlComModuleRegisterServer` provede mapování objektu automaticky generované knihovny ATL a zaregistruje každý objekt v objektu map. Pokud *pCLSID* není NULL, pak pouze objekt, na které odkazuje *pCLSID* zaregistrován; v opačném případě všechny objekty jsou registrované.

Tato funkce je volána [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver).

##  <a name="atlcommoduleunregisterserver"></a>  AtlComModuleUnregisterServer

Voláním této funkce se zruší registrace všech objektů v mapě objektů.

```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>Parametry

*pComModule*<br/>
Ukazatel na modulu COM.

*bUnRegTypeLib*<br/>
TRUE, pokud knihovna typů je k registraci.

*pCLSID*<br/>
Odkazuje na identifikátor CLSID objekt, který má být zrušena registrace. Pokud má hodnotu NULL bude zrušena všechny objekty v mapě objektů.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

`AtlComModuleUnregisterServer` provede mapování objektu ATL a zruší registraci jednotlivých objektů v mapě. Pokud *pCLSID* není NULL, pak pouze objekt, na které odkazuje *pCLSID* jinak zrušit všechny objekty jsou odregistrovat.

Tato funkce je volána [CAtlComModule::UnregisterServer](catlcommodule-class.md#unregisterserver).

##  <a name="atlcommoduleregisterclassobjects"></a>  AtlComModuleRegisterClassObjects

Voláním této funkce se zaregistrují objekty třídy.

```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*pComModule*<br/>
Ukazatel na modulu COM.

*dwClsContext*<br/>
Určuje kontext, ve kterém má být spuštěn objektu třídy. Možné hodnoty jsou CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER nebo CLSCTX_LOCAL_SERVER. Zobrazit [CLSCTX](/windows/desktop/api/wtypesbase/ne-wtypesbase-tagclsctx) další podrobnosti.

*dwFlags*<br/>
Určuje typy připojení k objektu třídy. Možné hodnoty jsou REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE nebo REGCLS_MULTI_SEPARATE. Zobrazit [REGCLS](/windows/desktop/api/combaseapi/ne-combaseapi-tagregcls) další podrobnosti.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využíváno [CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) (v ATL 7.0 zastaralé) a [CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects).

##  <a name="atlcommodulerevokeclassobjects"></a>  AtlComModuleRevokeClassObjects

Voláním této funkce se z tabulky spuštěných objektů odeberou objekty pro vytváření tříd.

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>Parametry

*pComModule*<br/>
Ukazatel na modulu COM.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využíváno [CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (v ATL 7.0 zastaralé) a [CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects).

##  <a name="atlcommodulegetclassobject"></a>  AtlComModuleGetClassObject

Voláním této funkce se vrátí objekt pro vytváření tříd.

```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```

### <a name="parameters"></a>Parametry

*pComModule*<br/>
Ukazatel na modulu COM.

*rclsid*<br/>
Identifikátor CLSID objektu, který má být vytvořen.

*riid*<br/>
Identifikátor IID požadované rozhraní.

*ppv*<br/>
Ukazatel na ukazatel rozhraní, který je identifikován *riid*. Pokud objekt nepodporuje toto rozhraní *ppv* nastaven na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využíváno [CComModule::GetClassObject](ccommodule-class.md#getclassobject) (v ATL 7.0 zastaralé) a [CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject).

## <a name="see-also"></a>Viz také

[Funkce](../../atl/reference/atl-functions.md)
