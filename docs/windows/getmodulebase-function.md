---
title: Getmodulebase – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
dev_langs:
- C++
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4d460b006d2d17df308a62c0433621aac7008f4d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411407"
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