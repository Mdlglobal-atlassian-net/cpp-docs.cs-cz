---
title: CancelTransitionPolicy – výčet
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
helpviewer_keywords:
- CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
ms.openlocfilehash: 99ca0c475d7fe700c2350ae05a87b8e64b10d775
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509964"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy – výčet

Určuje, jak asynchronní operace je pokus o přechod do konečný stav Dokončeno nebo chyba by se měly chovat s ohledem na klient vyžádal zrušeném stavu.

## <a name="syntax"></a>Syntaxe

```cpp
enum CancelTransitionPolicy;
```

## <a name="members"></a>Členové

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`RemainCanceled`|Pokud asynchronní operace je aktuálně ve zrušeném stavu klient vyžádal, to znamená, že zůstanou ve zrušeném stavu na rozdíl od přechod k dokončení terminálu nebo v chybovém stavu.|
|`TransitionFromCanceled`|Pokud asynchronní operace je aktuálně ve zrušeném stavu klient vyžádal, to znamená, že stav by měl přejít od zrušeném stavu na konečný stav Dokončeno nebo chyba, počítáno od volání, které používá tento příznak.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)