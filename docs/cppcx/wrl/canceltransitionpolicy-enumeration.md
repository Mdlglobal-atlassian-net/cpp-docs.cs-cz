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
ms.openlocfilehash: cb07f28794d466dde08719057a21ebf62f989e85
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398755"
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

## <a name="see-also"></a>Viz také:

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)