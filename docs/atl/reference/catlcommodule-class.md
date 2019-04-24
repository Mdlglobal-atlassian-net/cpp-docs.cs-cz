---
title: CAtlComModule Class
ms.date: 11/04/2016
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
ms.openlocfilehash: 09adcb33ca9e6f8524063130d6aedca044d6ecb5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247188"
---
# <a name="catlcommodule-class"></a>CAtlComModule Class

Tato třída implementuje modul COM serveru.

## <a name="syntax"></a>Syntaxe

```
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlComModule::CAtlComModule](#catlcommodule)|Konstruktor|
|[CAtlComModule::~CAtlComModule](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlComModule::RegisterServer](#registerserver)|Volejte tuto metodu za účelem aktualizace systémového registru pro jednotlivé objekty v mapě objektů.|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Volání této metody registrace knihovny typů.|
|[CAtlComModule::UnregisterServer](#unregisterserver)|Voláním této metody lze zrušit registraci jednotlivých objektů v mapě objektů.|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Voláním této metody lze zrušit registraci knihovny typů.|

## <a name="remarks"></a>Poznámky

`CAtlComModule` implementuje server modulu COM, umožňuje klientům přístup k součástem modulu.

Nahradí tato třída zastaralá [ccommodule –](../../atl/reference/ccommodule-class.md) třída používaná v dřívějších verzích ATL. Zobrazit [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="catlcommodule"></a>  CAtlComModule::CAtlComModule

Konstruktor

```
CAtlComModule() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje modul.

##  <a name="dtor"></a>  CAtlComModule::~CAtlComModule

Destruktor.

```
~CAtlComModule();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny objekty pro vytváření tříd.

##  <a name="registerserver"></a>  CAtlComModule::RegisterServer

Volejte tuto metodu za účelem aktualizace systémového registru pro jednotlivé objekty v mapě objektů.

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
TRUE, pokud knihovna typů je k registraci. Výchozí hodnota je FALSE.

*pCLSID*<br/>
Odkazuje na identifikátor CLSID objekt, který má být zaregistrován. Pokud se zaregistruje NULL (výchozí hodnota), všechny objekty v mapě objektů.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá funkci globální [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).

##  <a name="registertypelib"></a>  CAtlComModule::RegisterTypeLib

Volání této metody registrace knihovny typů.

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Řetězec ve formátu "\\\N", kde N je celočíselný index prostředku knihovny typů.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Přidá informace o knihovnu typů do systémového registru. Pokud instance modulu obsahuje více knihoven typů, použijte k určení, které knihovna typů by měla sloužit první verzi této metody.

##  <a name="unregisterserver"></a>  CAtlComModule::UnregisterServer

Voláním této metody lze zrušit registraci jednotlivých objektů v mapě objektů.

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
Hodnota TRUE, pokud má být zrušena registrace knihovny typů. Výchozí hodnota je FALSE.

*pCLSID*<br/>
Odkazuje na identifikátor CLSID objekt, který má být zrušena registrace. Pokud hodnotu NULL (výchozí hodnota), všechny objekty v mapě objektů bude zrušena.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá funkci globální [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

##  <a name="unregistertypelib"></a>  CAtlComModule::UnRegisterTypeLib

Voláním této metody lze zrušit registraci knihovny typů.

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Řetězec ve formátu "\\\N", kde N je celočíselný index prostředku knihovny typů.

### <a name="remarks"></a>Poznámky

Informace o knihovnu typů se odebere ze systémového registru. Pokud instance modulu obsahuje více knihoven typů, použijte k určení, které knihovna typů by měla sloužit první verzi této metody.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

## <a name="see-also"></a>Viz také:

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
