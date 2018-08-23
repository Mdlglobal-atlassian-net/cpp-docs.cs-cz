---
title: Creatormap – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
dev_langs:
- C++
helpviewer_keywords:
- CreatorMap structure
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0a622eaa40cedfd7bf22259cf81382290f20f3a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593731"
---
# <a name="creatormap-structure"></a>CreatorMap – struktura

Podporuje knihovny šablon jazyka C++ Windows Runtime infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>Poznámky

Obsahuje informace o tom, jak inicializovat, vytvářet a rušit registraci objektů.

**Creatormap –** obsahuje následující informace:

- Tom, jak inicializovat, vytvářet a rušit registraci objektů.

- Jak porovnat data aktivace v závislosti na objekt klasického modelu COM nebo prostředí Windows Runtime.

- Informace o název objektu pro vytváření mezipaměti a server pro rozhraní.

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CreatorMap::activationId – datový člen](../windows/creatormap-activationid-data-member.md)|Představuje ID objektu, který je identifikován classic ID třídy modelu COM nebo názvu modulu Windows Runtime.|
|[CreatorMap::factoryCache – datový člen](../windows/creatormap-factorycache-data-member.md)|Ukládá ukazatel na objekt pro vytváření mezipaměti **creatormap –**.|
|[CreatorMap::factoryCreator – datový člen](../windows/creatormap-factorycreator-data-member.md)|Vytvoří objekt factory pro zadaný **creatormap –**.|
|[CreatorMap::serverName – datový člen](../windows/creatormap-servername-data-member.md)|Ukládá název serveru pro **creatormap –**.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CreatorMap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)