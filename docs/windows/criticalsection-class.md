---
title: Criticalsection – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection class
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cab1beeaa3ce54899d1a052e4972bd7e7f52bb57
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592446"
---
# <a name="criticalsection-class"></a>CriticalSection – třída

Představuje objekt kritický oddíl.

## <a name="syntax"></a>Syntaxe

```cpp
class CriticalSection;
```

## <a name="members"></a>Členové

### <a name="constructor"></a>Konstruktor

|Název|Popis|
|----------|-----------------|
|[CriticalSection::CriticalSection – konstruktor](../windows/criticalsection-criticalsection-constructor.md)|Inicializuje objekt synchronizace, který je podobný objektu mutex, ale může využívat pouze vláken v jednom procesu.|
|[CriticalSection::~CriticalSection – destruktor](../windows/criticalsection-tilde-criticalsection-destructor.md)|Uvolní a odstraní aktuální **CriticalSection** objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CriticalSection::TryLock – metoda](../windows/criticalsection-trylock-method.md)|Pokusy o zadání kritický oddíl bez blokování. Pokud je volání úspěšné, volající vlákno trvá vlastnictví kritický oddíl.|
|[CriticalSection::Lock – metoda](../windows/criticalsection-lock-method.md)|Čeká na vlastnictví objektu zadaného kritický oddíl. Funkce vrátí, pokud volající vlákno bylo uděleno vlastnictví.|
|[CriticalSection::IsValid – metoda](../windows/criticalsection-isvalid-method.md)|Označuje, zda aktuální kritický oddíl je platný.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CriticalSection::cs_ – datový člen](../windows/criticalsection-cs-data-member.md)|Deklaruje datový člen kritický oddíl.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CriticalSection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)