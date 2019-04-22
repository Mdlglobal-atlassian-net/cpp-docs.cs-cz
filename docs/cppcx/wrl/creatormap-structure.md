---
title: CreatorMap – struktura
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
- module/Microsoft::WRL::Details::CreatorMap::activationId
- module/Microsoft::WRL::Details::CreatorMap::factoryCache
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
- module/Microsoft::WRL::Details::CreatorMap::serverName
helpviewer_keywords:
- Microsoft::WRL::Details::CreatorMap structure
- Microsoft::WRL::Details::CreatorMap::activationId data member
- Microsoft::WRL::Details::CreatorMap::factoryCache data member
- Microsoft::WRL::Details::CreatorMap::factoryCreator data member
- Microsoft::WRL::Details::CreatorMap::serverName data member
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
ms.openlocfilehash: 44d06f317661059bea92d8c6f27955606a964bb7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786734"
---
# <a name="creatormap-structure"></a>CreatorMap – struktura

Podporuje knihovny šablon jazyka C++ Windows Runtime infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>Poznámky

Obsahuje informace o tom, jak inicializovat, vytvářet a rušit registraci objektů.

`CreatorMap` obsahuje následující informace:

- Tom, jak inicializovat, vytvářet a rušit registraci objektů.

- Jak porovnat data aktivace v závislosti na objekt klasického modelu COM nebo prostředí Windows Runtime.

- Informace o název objektu pro vytváření mezipaměti a server pro rozhraní.

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

Name                                          | Popis
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[CreatorMap::activationId](#activationid)     | Představuje ID objektu, který je identifikován classic ID třídy modelu COM nebo názvu modulu Windows Runtime.
[CreatorMap::factoryCache](#factorycache)     | Ukládá ukazatel na objekt pro vytváření mezipaměti `CreatorMap`.
[CreatorMap::factoryCreator](#factorycreator) | Vytvoří objekt factory pro zadaný `CreatorMap`.
[CreatorMap::serverName](#servername)         | Ukládá název serveru pro `CreatorMap`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CreatorMap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="activationid"></a>CreatorMap::activationId

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>Parametry

*clsid*<br/>
Identifikátor rozhraní.

*getRuntimeName*<br/>
Funkce, která načte název modulu runtime Windows objektu.

### <a name="remarks"></a>Poznámky

Představuje ID objektu, který je identifikován classic ID třídy modelu COM nebo název modulu runtime Windows.

## <a name="factorycache"></a>CreatorMap::factoryCache

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>Poznámky

Ukládá ukazatel na objekt pro vytváření mezipaměti `CreatorMap`.

## <a name="factorycreator"></a>CreatorMap::factoryCreator

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>Parametry

*currentflags*<br/>
Jeden z [runtimeclasstype –](runtimeclasstype-enumeration.md) enumerátory.

*entry*<br/>
A CreatorMap.

*iidClassFactory*<br/>
ID rozhraní objekt pro vytváření tříd.

*objekt pro vytváření*<br/>
Po dokončení operace, adresa objektu pro vytváření tříd.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

### <a name="remarks"></a>Poznámky

Vytvoří objekt pro vytváření pro zadaný creatormap –.

## <a name="servername"></a>CreatorMap::serverName

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>Poznámky

Ukládá creatormap – název serveru.
