---
title: Catlcommodule – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
dev_langs:
- C++
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0600476df22c3d87bc5694e9ffe2af09f4542439
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063260"
---
# <a name="catlcommodule-class"></a>Catlcommodule – třída

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
|[Catlcommodule –:: ~ catlcommodule –](#dtor)|Destruktor.|

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

##  <a name="dtor"></a>  Catlcommodule –:: ~ catlcommodule –

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

## <a name="see-also"></a>Viz také

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
