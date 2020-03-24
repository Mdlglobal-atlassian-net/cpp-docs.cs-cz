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
ms.openlocfilehash: e820b3fffb4a00e95a1210a5c0beb3229c6d1657
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214120"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy – výčet

Určuje, jak se má při pokusu o přechod asynchronní operace přejít do stavu terminálu dokončeno nebo chyba, vzhledem k zrušenému stavu požadovanému klientem.

## <a name="syntax"></a>Syntaxe

```cpp
enum CancelTransitionPolicy;
```

## <a name="members"></a>Členové

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`RemainCanceled`|Pokud je asynchronní operace aktuálně ve zrušeném stavu, který byl vyžádán klientem, znamená to, že zůstane ve zrušeném stavu, nikoli při přechodu do terminálu dokončeného nebo chybového stavu.|
|`TransitionFromCanceled`|Pokud je asynchronní operace aktuálně ve zrušeném stavu, který byl vyžádán klientem, znamená to, že stav by měl přejít z stavu zrušeno do stavu terminálu dokončeno nebo chyba podle volání, které využívá tento příznak.|

## <a name="requirements"></a>Požadavky

**Hlavička:** Async. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)
