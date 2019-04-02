---
title: GetModuleBase – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 4d8c8467b7aeb9c21bf5f4ee19c60e6e60880688
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786608"
---
# <a name="getmodulebase-function"></a>Getmodulebase – funkce

Načte [ModuleBase](modulebase-class.md) ukazatel, který umožňuje zvyšování a dekrementace počet odkazů [RuntimeClass](runtimeclass-class.md) objektu.

## <a name="syntax"></a>Syntaxe

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel `ModuleBase` objektu.

## <a name="remarks"></a>Poznámky

Tato funkce se používá interně ke addref() vrátí odkaz na objekt.

Tuto funkci můžete použít k řízení počty odkazů voláním [modulebase::incrementobjectcount –](modulebase-class.md#incrementobjectcount) a [modulebase::decrementobjectcount –](modulebase-class.md#decrementobjectcount).

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také:

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)