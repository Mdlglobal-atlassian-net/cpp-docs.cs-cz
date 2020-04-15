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
ms.openlocfilehash: 1527f81694d1d809d585f3f6504c0e6433a2c26b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372605"
---
# <a name="creatormap-structure"></a>CreatorMap – struktura

Podporuje infrastrukturu knihovny šablon prostředí Prostředí Windows Runtime C++ a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>Poznámky

Obsahuje informace o tom, jak inicializovat, registrovat a zrušit registraci objektů.

`CreatorMap`obsahuje tyto informace:

- Jak inicializovat, registrovat a zrušit registraci objektů.

- Jak porovnat aktivační data v závislosti na klasické matné službě COM nebo Windows Runtime factory.

- Informace o mezipaměti výroby a názvu serveru pro rozhraní.

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

Name (Název)                                          | Popis
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[CreatorMap::activationId](#activationid)     | Představuje ID objektu, který je identifikován buď klasické id třídy COM nebo název prostředí Windows Runtime.
[CreatorMap::factoryCache](#factorycache)     | Uloží ukazatel do mezipaměti `CreatorMap`továrny pro .
[CreatorMap::factoryCreator](#factorycreator) | Vytvoří továrnu pro `CreatorMap`zadanou .
[CreatorMap::název_serveru](#servername)         | Uloží název serveru `CreatorMap`pro .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CreatorMap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="creatormapactivationid"></a><a name="activationid"></a>CreatorMap::activationId

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>Parametry

*Identifikátor clsid*<br/>
ID rozhraní.

*getRuntimeName*<br/>
Funkce, která načte název objektu za běhu systému Windows.

### <a name="remarks"></a>Poznámky

Představuje ID objektu, který je identifikován buď klasickým ID třídy COM nebo názvem prostředí runtime systému Windows.

## <a name="creatormapfactorycache"></a><a name="factorycache"></a>CreatorMap::factoryCache

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>Poznámky

Uloží ukazatel do mezipaměti `CreatorMap`továrny pro .

## <a name="creatormapfactorycreator"></a><a name="factorycreator"></a>CreatorMap::factoryCreator

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>Parametry

*currentflags*<br/>
Jeden z čítačů výčtu [RuntimeClassType.](runtimeclasstype-enumeration.md)

*Položka*<br/>
Mapa tvůrců.

*IidClassFactory*<br/>
ID rozhraní třídy factory.

*Továrna*<br/>
Po dokončení operace, adresa factory třídy.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

### <a name="remarks"></a>Poznámky

Vytvoří továrnu pro zadaný CreatorMap.

## <a name="creatormapservername"></a><a name="servername"></a>CreatorMap::název_serveru

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>Poznámky

Ukládá název serveru pro CreatorMap.
