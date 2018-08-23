---
title: Criticalsection::Lock – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 37cb184c-e13c-49ef-b6a0-13908a956414
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4fedde29441c9c14b68dec5cff998be57d216e29
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607657"
---
# <a name="criticalsectionlock-method"></a>CriticalSection::Lock – metoda

Čeká na vlastnictví objektu zadaného kritický oddíl. Funkce vrátí, pokud volající vlákno bylo uděleno vlastnictví.

## <a name="syntax"></a>Syntaxe

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parametry

*cs*  
Kritický oddíl uživatelem zadaného objektu.

## <a name="return-value"></a>Návratová hodnota

Zamknout objekt, který můžete použít k odemknutí aktuální kritický oddíl.

## <a name="remarks"></a>Poznámky

První **Zámek** aktuální objekt kritický oddíl má vliv na funkce. Druhá **Zámek** funkce ovlivňuje kritickou sekci zadané uživatelem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[CriticalSection – třída](../windows/criticalsection-class.md)