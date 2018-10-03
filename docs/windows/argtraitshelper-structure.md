---
title: Argtraitshelper – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
- event/Microsoft::WRL::Details::ArgTraitsHelper::args
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraitsHelper structure
- Microsoft::WRL::Details::ArgTraitsHelper::args constant
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b608f5da893019d7700891968dcdc06489c563ea
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234226"
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

**Namespace:** Microsoft::WRL:: details –

## <a name="args"></a>ArgTraitsHelper::args

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>Poznámky

Pomáhá `ArgTraitsHelper::args` zachovat počet parametrů na `Invoke` metoda rozhraní delegáta.
