---
title: CAtlComModule – třída
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
ms.openlocfilehash: 4b8c98630b27c35ed6a7e32318c6ebad8a82a5c5
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168815"
---
# <a name="catlcommodule-class"></a>CAtlComModule – třída

Tato třída implementuje modul COM serveru.

## <a name="syntax"></a>Syntaxe

```cpp
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlComModule::CAtlComModule](#catlcommodule)|Konstruktor|
|[CAtlComModule:: ~ CAtlComModule](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlComModule::RegisterServer](#registerserver)|Voláním této metody aktualizujete systémový registr pro každý objekt v mapě objektů.|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Voláním této metody zaregistrujete knihovnu typů.|
|[CAtlComModule::UnregisterServer](#unregisterserver)|Voláním této metody zrušíte registraci každého objektu v mapě objektů.|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Voláním této metody zrušíte registraci knihovny typů.|

## <a name="remarks"></a>Poznámky

`CAtlComModule`implementuje modul COM serveru a umožňuje klientovi přístup k součástem modulu.

Tato třída nahrazuje zastaralou třídu [CComModule](../../atl/reference/ccommodule-class.md) , která se používá v dřívějších verzích knihovny ATL. Další podrobnosti naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="catlcommodulecatlcommodule"></a><a name="catlcommodule"></a>CAtlComModule::CAtlComModule

Konstruktor

```cpp
CAtlComModule() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje modul.

## <a name="catlcommodulecatlcommodule"></a><a name="dtor"></a>CAtlComModule:: ~ CAtlComModule

Destruktor.

```cpp
~CAtlComModule();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny továrny tříd.

## <a name="catlcommoduleregisterserver"></a><a name="registerserver"></a>CAtlComModule::RegisterServer

Voláním této metody aktualizujete systémový registr pro každý objekt v mapě objektů.

```cpp
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
TRUE, pokud má být zaregistrována knihovna typů. Výchozí hodnota je FALSE (NEPRAVDA).

*pCLSID*<br/>
Odkazuje na CLSID objektu, který má být zaregistrován. Pokud má hodnotu NULL (výchozí hodnota), budou zaregistrovány všechny objekty v mapě objektů.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá globální funkci [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).

## <a name="catlcommoduleregistertypelib"></a><a name="registertypelib"></a>CAtlComModule::RegisterTypeLib

Voláním této metody zaregistrujete knihovnu typů.

```cpp
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Řetězec ve formátu "\\\n", kde N je celočíselný index prostředku TYPELIB.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Přidá do systémového registru informace o knihovně typů. Pokud instance modulu obsahuje více knihoven typů, použijte první verzi této metody k určení, která knihovna typů má být použita.

## <a name="catlcommoduleunregisterserver"></a><a name="unregisterserver"></a>CAtlComModule::UnregisterServer

Voláním této metody zrušíte registraci každého objektu v mapě objektů.

```cpp
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
TRUE, pokud má být zrušena registrace knihovny typů. Výchozí hodnota je FALSE (NEPRAVDA).

*pCLSID*<br/>
Odkazuje na CLSID objektu, který se má odregistrovat. Pokud má hodnotu NULL (výchozí hodnota), všechny objekty v mapě objektů budou odregistrovány.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá globální funkci [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

## <a name="catlcommoduleunregistertypelib"></a><a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib

Voláním této metody zrušíte registraci knihovny typů.

```cpp
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Řetězec ve formátu "\\\n", kde N je celočíselný index prostředku TYPELIB.

### <a name="remarks"></a>Poznámky

Odebere informace o knihovně typů ze systémového registru. Pokud instance modulu obsahuje více knihoven typů, použijte první verzi této metody k určení, která knihovna typů má být použita.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

## <a name="see-also"></a>Viz také

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
