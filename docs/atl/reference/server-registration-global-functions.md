---
title: Globální funkce registrace serveru
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
ms.openlocfilehash: f9c3697259e1cee2b1107ded785ca583d730b55e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495466"
---
# <a name="server-registration-global-functions"></a>Globální funkce registrace serveru

Tyto funkce poskytují podporu pro registraci a zrušení registrace objektů serveru v mapě objektů.

> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

|||
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|Voláním této funkce se zaregistrují všechny objekty v mapě objektů.|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|Voláním této funkce se zruší registrace všech objektů v mapě objektů.|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|Voláním této funkce se zaregistrují objekty třídy.|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|Tato funkce je volána pro odvolání objektů třídy z modulu COM.|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|Tato funkce je volána pro získání objektu třídy.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

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
Ukazatel na modul COM.

*bRegTypeLib*<br/>
TRUE, pokud má být zaregistrována knihovna typů.

*pCLSID*<br/>
Odkazuje na CLSID objektu, který má být zaregistrován. Pokud má hodnotu NULL, všechny objekty v mapě objektů budou zaregistrovány.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

`AtlComModuleRegisterServer`provede mapování automaticky generovaného objektu knihovny ATL a zaregistruje všechny objekty v mapě. Pokud *pCLSID* není null, pak je zaregistrován pouze objekt, na který odkazuje *pCLSID* . jinak jsou všechny objekty registrovány.

Tato funkce je volána funkcí [CAtlComModule:: RegisterServer](catlcommodule-class.md#registerserver).

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
Ukazatel na modul COM.

*bUnRegTypeLib*<br/>
TRUE, pokud má být zaregistrována knihovna typů.

*pCLSID*<br/>
Odkazuje na CLSID objektu, který se má odregistrovat. Pokud je hodnota NULL všech objektů v mapě objektů zaregistrována.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

`AtlComModuleUnregisterServer`provede mapování objektů ATL a zruší registraci každého objektu v mapě. Pokud *pCLSID* není null, pak pouze objekt, na který odkazuje *pCLSID* , není zaregistrován; jinak se zruší registrace všech objektů.

Tato funkce je volána funkcí [CAtlComModule:: UnregisterServer](catlcommodule-class.md#unregisterserver).

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
Ukazatel na modul COM.

*dwClsContext*<br/>
Určuje kontext, ve kterém má být objekt třídy spuštěn. Možné hodnoty jsou CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER nebo CLSCTX_LOCAL_SERVER. Další podrobnosti najdete v tématu [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) .

*dwFlags*<br/>
Určuje typy připojení k objektu třídy. Možné hodnoty jsou REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE nebo REGCLS_MULTI_SEPARATE. Další podrobnosti najdete v tématu [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využívána pomocí [CComModule:: RegisterClassObjects](ccommodule-class.md#registerclassobjects) (zastaralé v knihovně ATL 7,0) a [CAtlExeModuleT:: RegisterClassObjects](catlexemodulet-class.md#registerclassobjects).

##  <a name="atlcommodulerevokeclassobjects"></a>  AtlComModuleRevokeClassObjects

Voláním této funkce se z tabulky spuštěných objektů odeberou objekty pro vytváření tříd.

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>Parametry

*pComModule*<br/>
Ukazatel na modul COM.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využívána pomocí [CComModule:: RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (zastaralé v knihovně ATL 7,0) a [CAtlExeModuleT:: RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects).

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

*pComModule*<br/>
Ukazatel na modul COM.

*rclsid*<br/>
Identifikátor CLSID objektu, který má být vytvořen.

*riid*<br/>
IID požadovaného rozhraní.

*ppv*<br/>
Ukazatel na ukazatel rozhraní identifikovaný *riid*. Pokud objekt nepodporuje toto rozhraní, je *PPV* nastaveno na hodnotu null.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využívána pomocí [CComModule:: GetClassObject –](ccommodule-class.md#getclassobject) (zastaralé v knihovně ATL 7,0) a [CAtlDllModuleT:: GetClassObject –](catldllmodulet-class.md#getclassobject).

## <a name="see-also"></a>Viz také:

[Funkce](../../atl/reference/atl-functions.md)
