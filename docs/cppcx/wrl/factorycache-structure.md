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
ms.openlocfilehash: 507d35179b9fa86399e56b18171800f41eaf1f10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371494"
---
# <a name="factorycache-structure"></a>FactoryCache – struktura

Podporuje infrastrukturu knihovny šablon prostředí Prostředí Windows Runtime C++ a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>Poznámky

Obsahuje umístění factory třídy a hodnotu, která identifikuje registrovaný objekt třídy WRT nebo COM.

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

Name (Název)                              | Popis
--------------------------------- | ------------------------------------------------------------------------------------------------------------------------------
[FactoryCache::soubor cookie](#cookie)   | Obsahuje hodnotu, která identifikuje registrovaný objekt třídy Windows Runtime nebo COM a později se používá k zrušení registrace objektu.
[FactoryCache::factory](#factory) | Odkazuje na systém Windows Runtime nebo com třídy factory.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`FactoryCache`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="factorycachecookie"></a><a name="cookie"></a>FactoryCache::soubor cookie

Podporuje infrastrukturu knihovny šablon prostředí Prostředí Windows Runtime C++ a není určen pro použití přímo z vašeho kódu.

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

### <a name="remarks"></a>Poznámky

Obsahuje hodnotu, která identifikuje registrovaný objekt třídy Windows Runtime nebo COM a později se používá k zrušení registrace objektu.

## <a name="factorycachefactory"></a><a name="factory"></a>FactoryCache::factory

Podporuje infrastrukturu knihovny šablon prostředí Prostředí Windows Runtime C++ a není určen pro použití přímo z vašeho kódu.

```cpp
IUnknown* factory;
```

### <a name="remarks"></a>Poznámky

Odkazuje na systém Windows Runtime nebo com třídy factory.
