---
title: DontUseNewUseMake – třída
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
ms.openlocfilehash: 02420f2657c7d7d6a7a0294f0321717a3bb2b5d7
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334766"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Poznámky

Brání použití operátoru `new` v `RuntimeClass`. V důsledku toho je nutné použít [Make – funkce](make-function.md) místo.

## <a name="members"></a>Členové

### <a name="public-operators"></a>Veřejné operátory

Název                                             | Popis
------------------------------------------------ | ---------------------------------------------------------------------------
[DontUseNewUseMake::operator nové](#operator-new) | Přetížení operátoru `new` a brání použití v `RuntimeClass`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`DontUseNewUseMake`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="operator-new"></a>DontUseNewUseMake::operator nové

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>Parametry

*__unnamed0*<br/>
Nepojmenovaný parametr, který určuje počet bajtů paměti k přidělení.

*placement*<br/>
Typ, který má být přiděleny.

### <a name="return-value"></a>Návratová hodnota

Poskytuje způsob, jak předat další argumenty, pokud přetížíte operátor `new`.

### <a name="remarks"></a>Poznámky

Přetížení operátoru `new` a brání použití v `RuntimeClass`.
