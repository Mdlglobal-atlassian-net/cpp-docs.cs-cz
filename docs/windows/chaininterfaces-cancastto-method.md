---
title: Chaininterfaces::cancastto – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 8be44875-53ed-494b-91a0-0f8e399685bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 752c3598a38117506154b0a2b7d7d3e578bf3c3e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417641"
---
# <a name="chaininterfacescancastto-method"></a>ChainInterfaces::CanCastTo – metoda

Určuje, zda ID zadané rozhraní může být převeden na jednotlivé specializace určené parametry jiné než výchozí šablony.

## <a name="syntax"></a>Syntaxe

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identifikátor rozhraní.

*ppv*<br/>
Ukazatel na poslední ID rozhraní, který byl úspěšně převeden.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud všechny operace přetypování bylo úspěšné; jinak **false**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[ChainInterfaces – struktura](../windows/chaininterfaces-structure.md)