---
title: Factorycache – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
dev_langs:
- C++
helpviewer_keywords:
- FactoryCache structure
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: df2335a49d2d5daf862db7cea7eb413c01164bee
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609025"
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

|Název|Popis|
|----------|-----------------|
|[FactoryCache::cookie – datový člen](../windows/factorycache-cookie-data-member.md)|Obsahuje hodnotu, která identifikuje registrovaného objektu třídy Windows Runtime nebo modelu COM a je později použít ke zrušení registrace objektu.|
|[FactoryCache::factory – datový člen](../windows/factorycache-factory-data-member.md)|Odkazuje na objekt třídy Windows Runtime nebo modelu COM.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`FactoryCache`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)