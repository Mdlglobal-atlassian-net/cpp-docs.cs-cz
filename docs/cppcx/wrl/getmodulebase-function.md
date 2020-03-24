---
title: GetModuleBase – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 0d130fffa9fad9ae327d03eaa01d84742094cc67
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213964"
---
# <a name="getmodulebase-function"></a>GetModuleBase – funkce

Načte ukazatel [ModuleBase](modulebase-class.md) , který umožňuje zvýšit a snížit počet odkazů objektu [RuntimeClass](runtimeclass-class.md) .

## <a name="syntax"></a>Syntaxe

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `ModuleBase`.

## <a name="remarks"></a>Poznámky

Tato funkce se interně používá ke zvýšení a snížení počtu odkazů na objekty.

Pomocí této funkce lze řídit počty odkazů voláním [ModuleBase:: IncrementObjectCount –](modulebase-class.md#incrementobjectcount) a [ModuleBase::D ecrementobjectcount](modulebase-class.md#decrementobjectcount).

## <a name="requirements"></a>Požadavky

**Hlavička:** Implements. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)
