---
title: Dontusenewusemake – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9c1f3a57401a3ab2efd45cab2dace127010c24e6
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235279"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Poznámky

Brání použití operátoru `new` v `RuntimeClass`. V důsledku toho je nutné použít [Make – funkce](../windows/make-function.md) místo.

## <a name="members"></a>Členové

### <a name="public-operators"></a>Veřejné operátory

Název                                             | Popis
------------------------------------------------ | ---------------------------------------------------------------------------
[DontUseNewUseMake::operator nové](#operator-new) | Přetížení operátoru `new` a brání použití v `RuntimeClass`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`DontUseNewUseMake`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

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

*umístění*<br/>
Typ, který má být přiděleny.

### <a name="return-value"></a>Návratová hodnota

Poskytuje způsob, jak předat další argumenty, pokud přetížíte operátor `new`.

### <a name="remarks"></a>Poznámky

Přetížení operátoru `new` a brání použití v `RuntimeClass`.
