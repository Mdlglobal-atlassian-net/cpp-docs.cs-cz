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
ms.openlocfilehash: fb6353b52f487d0511c54223fe9e31dab88704b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325932"
---
# <a name="server-registration-global-functions"></a>Globální funkce registrace serveru

Tyto funkce poskytují podporu pro registraci a zrušení registrace objektů serveru v mapě objektů.

> [!IMPORTANT]
> Funkce uvedené v následující tabulce nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

|||
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|Voláním této funkce se zaregistrují všechny objekty v mapě objektů.|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|Voláním této funkce se zruší registrace všech objektů v mapě objektů.|
|[Objekty AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|Voláním této funkce se zaregistrují objekty třídy.|
|[Objekty AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|Tato funkce je volána k odvolání objektů třídy z modulu COM.|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|Tato funkce je volána získat objekt třídy.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="atlcommoduleregisterserver"></a><a name="atlcommoduleregisterserver"></a>AtlComModuleRegisterServer

Voláním této funkce se zaregistrují všechny objekty v mapě objektů.

```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>Parametry

*modul pCom*<br/>
Ukazatel na modul COM.

*bRegTypeLib*<br/>
TRUE, pokud má být knihovna typů registrována.

*pCLSID*<br/>
Odkazuje na CLSID objektu, který má být registrován. Pokud null, všechny objekty v mapě objektu budou registrovány.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

`AtlComModuleRegisterServer`prochází mapu automaticky generovaných objektů ATL a registruje každý objekt v mapě. Pokud *hodnota pCLSID* není null, je registrován pouze objekt, na který odkazuje *identifikátor pCLSID;* jinak jsou registrovány všechny objekty.

Tato funkce je volána [catlcommodule::RegisterServer](catlcommodule-class.md#registerserver).

## <a name="atlcommoduleunregisterserver"></a><a name="atlcommoduleunregisterserver"></a>AtlComModuleUnregisterServer

Voláním této funkce se zruší registrace všech objektů v mapě objektů.

```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>Parametry

*modul pCom*<br/>
Ukazatel na modul COM.

*bUnRegTypeLib*<br/>
TRUE, pokud má být knihovna typů registrována.

*pCLSID*<br/>
Odkazuje na CLSID objektu, který má být neregistrován. Pokud null všechny objekty v mapě objektu bude unregistered.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

`AtlComModuleUnregisterServer`prochází mapu objektů KNIHOVNY ATL a zruší registrace každého objektu v mapě. Pokud *hodnota pCLSID* není null, není registrován pouze objekt, na který odkazuje *identifikátor pCLSID.* jinak jsou všechny objekty neregistrované.

Tato funkce je volána [modulem CAtlComModule::UnregisterServer](catlcommodule-class.md#unregisterserver).

## <a name="atlcommoduleregisterclassobjects"></a><a name="atlcommoduleregisterclassobjects"></a>Objekty AtlComModuleRegisterClassObjects

Voláním této funkce se zaregistrují objekty třídy.

```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*modul pCom*<br/>
Ukazatel na modul COM.

*dwClsKontext*<br/>
Určuje kontext, ve kterém má být objekt třídy spuštěn. Možné hodnoty jsou CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER nebo CLSCTX_LOCAL_SERVER. Další podrobnosti naleznete [v souboru CLSCTX.](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx)

*dwFlags*<br/>
Určuje typy připojení k objektu třídy. Možné hodnoty jsou REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE nebo REGCLS_MULTI_SEPARATE. Další podrobnosti naleznete [v části REGCLS.](/windows/win32/api/combaseapi/ne-combaseapi-regcls)

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využívána [CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) (zastaralé v ATL 7.0) a [CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects).

## <a name="atlcommodulerevokeclassobjects"></a><a name="atlcommodulerevokeclassobjects"></a>Objekty AtlComModuleRevokeClassObjects

Voláním této funkce se z tabulky spuštěných objektů odeberou objekty pro vytváření tříd.

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>Parametry

*modul pCom*<br/>
Ukazatel na modul COM.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využívána [CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (zastaralé v ATL 7.0) a [CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects).

## <a name="atlcommodulegetclassobject"></a><a name="atlcommodulegetclassobject"></a>AtlComModuleGetClassObject

Voláním této funkce se vrátí objekt pro vytváření tříd.

```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```

### <a name="parameters"></a>Parametry

*modul pCom*<br/>
Ukazatel na modul COM.

*rclsid (rclsid)*<br/>
CLSID objektu, který má být vytvořen.

*riid řekl:*<br/>
IID požadovanérozhraní.

*Ppv*<br/>
Ukazatel rozhraní určený *riid*. Pokud objekt nepodporuje toto rozhraní, *je hodnota ppv* nastavena na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využívána [CComModule::GetClassObject](ccommodule-class.md#getclassobject) (zastaralé v ATL 7.0) a [CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject).

## <a name="see-also"></a>Viz také

[Functions](../../atl/reference/atl-functions.md)
