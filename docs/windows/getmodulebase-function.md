---
title: GetModuleBase – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 40289903eba2ce7ac35d4d0b208c3b609efb09f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650811"
---
# <a name="getmodulebase-function"></a>GetModuleBase – funkce
Načte [ModuleBase](../windows/modulebase-class.md) ukazatel, který umožňuje zvyšování a dekrementace počet odkazů [RuntimeClass](../windows/runtimeclass-class.md) objektu.

## <a name="syntax"></a>Syntaxe

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel `ModuleBase` objektu.

## <a name="remarks"></a>Poznámky

Tato funkce se používá interně ke addref() vrátí odkaz na objekt.

Tuto funkci můžete použít k řízení počty odkazů voláním [modulebase::incrementobjectcount –](../windows/modulebase-incrementobjectcount-method.md) a [modulebase::decrementobjectcount –](../windows/modulebase-decrementobjectcount-method.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)