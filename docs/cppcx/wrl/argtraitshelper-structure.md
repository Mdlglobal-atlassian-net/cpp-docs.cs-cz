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
ms.openlocfilehash: 4acbd9fa660f29bbaf209282ff0e90f43621574d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360773"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper – struktura

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Rozhraní delegáta.

## <a name="remarks"></a>Poznámky

Pomáhá definovat společné charakteristiky argumentů delegáta.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

Name (Název)         | Popis
------------ | ------------------------------------------------------
`methodType` | Synonymum `decltype(&TDelegateInterface::Invoke)`pro .
`Traits`     | Synonymum `ArgTraits<methodType>`pro .

### <a name="public-constants"></a>Veřejné konstanty

Name (Název)                           | Popis
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[ArgTraitsHelper::args](#args) | Pomáhá [ArgTraits::args](#args) zachovat počet parametrů na `Invoke` metodu delegáta rozhraní.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ArgTraitsHelper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="argtraitshelperargs"></a><a name="args"></a>ArgTraitsHelper::args

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>Poznámky

Pomáhá `ArgTraitsHelper::args` udržovat počet parametrů na metodu `Invoke` delegáta rozhraní.
