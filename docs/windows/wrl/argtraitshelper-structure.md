---
title: ArgTraitsHelper – struktura
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
- event/Microsoft::WRL::Details::ArgTraitsHelper::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraitsHelper structure
- Microsoft::WRL::Details::ArgTraitsHelper::args constant
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
ms.openlocfilehash: fbba6d96106cc95910ccd9d0029cb3e9c254d7d3
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334910"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Rozhraní delegáta.

## <a name="remarks"></a>Poznámky

Pomáhá definovat běžné vlastnosti argumenty delegátů.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

Název         | Popis
------------ | ------------------------------------------------------
`methodType` | Synonymum pro `decltype(&TDelegateInterface::Invoke)`.
`Traits`     | Synonymum pro `ArgTraits<methodType>`.

### <a name="public-constants"></a>Veřejné konstanty

Název                           | Popis
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[ArgTraitsHelper::args](#args) | Pomáhá [ArgTraits::args](#args) zachovat počet parametrů na `Invoke` metoda rozhraní delegáta.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ArgTraitsHelper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="args"></a>ArgTraitsHelper::args

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>Poznámky

Pomáhá `ArgTraitsHelper::args` zachovat počet parametrů na `Invoke` metoda rozhraní delegáta.
