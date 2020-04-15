---
title: Třída CAtlComModule
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
ms.openlocfilehash: 68fdb48edc9304d9d74df6f36bd208cfd35ff307
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321486"
---
# <a name="catlcommodule-class"></a>Třída CAtlComModule

Tato třída implementuje serverový modul COM.

## <a name="syntax"></a>Syntaxe

```
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlComModule::CAtlComModule](#catlcommodule)|Konstruktor|
|[CAtlComModule::~CAtlComModule](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlComModule::RegisterServer](#registerserver)|Volání této metody aktualizovat systémový registr pro každý objekt v mapě objektu.|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Volání této metody zaregistrovat knihovnu typů.|
|[CAtlComModule::UnregisterServer](#unregisterserver)|Volání této metody zrušit registraci každého objektu v mapě objektu.|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Volání této metody zrušit registraci knihovny typů.|

## <a name="remarks"></a>Poznámky

`CAtlComModule`implementuje serverový modul COM, který umožňuje klientovi přístup ke komponentám modulu.

Tato třída nahrazuje zastaralou třídu [CComModule](../../atl/reference/ccommodule-class.md) používanou v dřívějších verzích atl. Další podrobnosti naleznete [v části Třídy modulů ATL.](../../atl/atl-module-classes.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="catlcommodulecatlcommodule"></a><a name="catlcommodule"></a>CAtlComModule::CAtlComModule

Konstruktor

```
CAtlComModule() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje modul.

## <a name="catlcommodulecatlcommodule"></a><a name="dtor"></a>CAtlComModule::~CAtlComModule

Destruktor.

```
~CAtlComModule();
```

### <a name="remarks"></a>Poznámky

Osvobozuje všechny třídní továrny.

## <a name="catlcommoduleregisterserver"></a><a name="registerserver"></a>CAtlComModule::RegisterServer

Volání této metody aktualizovat systémový registr pro každý objekt v mapě objektu.

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
TRUE, pokud má být knihovna typů registrována. Výchozí hodnota je FALSE.

*pCLSID*<br/>
Odkazuje na CLSID objektu, který má být registrován. Pokud null (výchozí hodnota), budou zaregistrovány všechny objekty v mapě objektů.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá globální funkci [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).

## <a name="catlcommoduleregistertypelib"></a><a name="registertypelib"></a>CAtlComModule::RegisterTypeLib

Volání této metody zaregistrovat knihovnu typů.

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Řetězec ve formátu\\\N, kde N je index celéčíslo prostředku TYPELIB.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Přidá informace o knihovně typů do systémového registru. Pokud instance modulu obsahuje více knihoven typů, použijte první verzi této metody k určení, která knihovna typů má být použita.

## <a name="catlcommoduleunregisterserver"></a><a name="unregisterserver"></a>CAtlComModule::UnregisterServer

Volání této metody zrušit registraci každého objektu v mapě objektu.

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
TRUE, pokud má být knihovna typů neregistrována. Výchozí hodnota je FALSE.

*pCLSID*<br/>
Odkazuje na CLSID objektu, který má být neregistrován. Pokud null (výchozí hodnota), všechny objekty v mapě objektu budou unregistered.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá globální funkci [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

## <a name="catlcommoduleunregistertypelib"></a><a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib

Volání této metody zrušit registraci knihovny typů.

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Řetězec ve formátu\\\N, kde N je index celéčíslo prostředku TYPELIB.

### <a name="remarks"></a>Poznámky

Odebere informace o knihovně typů ze systémového registru. Pokud instance modulu obsahuje více knihoven typů, použijte první verzi této metody k určení, která knihovna typů má být použita.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="see-also"></a>Viz také

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
