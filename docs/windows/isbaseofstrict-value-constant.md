---
title: IsBaseOfStrict::value – konstanta | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
dev_langs:
- C++
helpviewer_keywords:
- value constant
ms.assetid: 4a0cdab0-ba03-482b-babf-eeec519ba687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 65b69c974e74ff68a1af2e17ff1fc8f03e03e3af
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439286"
---
# <a name="isbaseofstrictvalue-constant"></a>IsBaseOfStrict::value – konstanta

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
static const bool value = __is_base_of(Base, Derived);
```

## <a name="remarks"></a>Poznámky

Označuje, zda je jeden typ základ jiného.

**Hodnota** je **true** Pokud typ `Base` je základní třídu typu `Derived`, v opačném případě je **false**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[IsBaseOfStrict – struktura](../windows/isbaseofstrict-structure.md)<br/>
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)