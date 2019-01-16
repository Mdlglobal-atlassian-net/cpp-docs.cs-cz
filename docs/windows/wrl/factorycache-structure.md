---
title: FactoryCache – struktura
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
- module/Microsoft::WRL::Details::FactoryCache::cookie
- module/Microsoft::WRL::Details::FactoryCache::factory
helpviewer_keywords:
- Microsoft::WRL::Details::FactoryCache structure
- Microsoft::WRL::Details::FactoryCache::cookie data member
- Microsoft::WRL::Details::FactoryCache::factory data member
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
ms.openlocfilehash: 7196363567dffa43844bbbd1de76934a317302d1
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334758"
---
# <a name="factorycache-structure"></a>FactoryCache – struktura

Podporuje knihovny šablon jazyka C++ Windows Runtime infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>Poznámky

Obsahuje umístění objektu pro vytváření tříd a hodnotu, která identifikuje registrovaný wrt nebo objektu třídy modelu COM.

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

Název                              | Popis
--------------------------------- | ------------------------------------------------------------------------------------------------------------------------------
[FactoryCache::cookie](#cookie)   | Obsahuje hodnotu, která identifikuje registrovaného objektu třídy Windows Runtime nebo modelu COM a je později použít ke zrušení registrace objektu.
[FactoryCache::factory](#factory) | Odkazuje na objekt třídy Windows Runtime nebo modelu COM.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`FactoryCache`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="cookie"></a>FactoryCache::cookie

Podporuje knihovny šablon jazyka C++ Windows Runtime infrastrukturu a není určena pro použití přímo v kódu.

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

### <a name="remarks"></a>Poznámky

Obsahuje hodnotu, která identifikuje registrovaného objektu třídy Windows Runtime nebo modelu COM a je později použít ke zrušení registrace objektu.

## <a name="factory"></a>FactoryCache::factory

Podporuje knihovny šablon jazyka C++ Windows Runtime infrastrukturu a není určena pro použití přímo v kódu.

```cpp
IUnknown* factory;
```

### <a name="remarks"></a>Poznámky

Odkazuje na objekt třídy Windows Runtime nebo modelu COM.
