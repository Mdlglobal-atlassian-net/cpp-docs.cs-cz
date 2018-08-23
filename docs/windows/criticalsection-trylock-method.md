---
title: Criticalsection::trylock – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs:
- C++
helpviewer_keywords:
- TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 382dbdd2d0816d6ab0846acd0f8c164cd542114f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575838"
---
# <a name="criticalsectiontrylock-method"></a>CriticalSection::TryLock – metoda

Pokusy o zadání kritický oddíl bez blokování. Pokud je volání úspěšné, volající vlákno trvá vlastnictví kritický oddíl.

## <a name="syntax"></a>Syntaxe

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parametry

*cs*  
Kritický oddíl uživatelem zadaného objektu.

## <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud byly úspěšně uloženy kritický oddíl nebo aktuální vlákno již vlastní kritický oddíl. Nula v případě jiné vlákno již vlastní kritický oddíl.

## <a name="remarks"></a>Poznámky

První **trylock –** aktuální objekt kritický oddíl má vliv na funkce. Druhá **trylock –** funkce ovlivňuje kritickou sekci zadané uživatelem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[CriticalSection – třída](../windows/criticalsection-class.md)