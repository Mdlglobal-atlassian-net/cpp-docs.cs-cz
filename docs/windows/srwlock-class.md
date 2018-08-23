---
title: Srwlock – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
dev_langs:
- C++
helpviewer_keywords:
- SRWLock class
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fb97a29796c287cfaadddc305f25807de5dcba2e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604233"
---
# <a name="srwlock-class"></a>Třída SRWLock

Představuje zámek tenký čtení/zápis.

## <a name="syntax"></a>Syntaxe

```cpp
class SRWLock;
```

## <a name="remarks"></a>Poznámky

Zámek tenký čtení/zápis se používá k synchronizaci přístupu napříč vlákny na objekt nebo prostředků. Další informace najdete v tématu [funkce synchronizace](/windows/desktop/Sync/synchronization-functions).

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|||
|-|-|
|`SyncLockExclusive`|Synonymum pro **SRWLock** objekt, který je požadován ve výhradním režimu.|
|`SyncLockShared`|Synonymum pro **SRWLock** objekt, který je požadován ve sdíleném režimu.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[SRWLock::SRWLock – konstruktor](../windows/srwlock-srwlock-constructor.md)|Inicializuje novou instanci třídy **SRWLock** třídy.|
|[SRWLock::~SRWLock – destruktor](../windows/srwlock-tilde-srwlock-destructor.md)|Uvolní instanci **SRWLock** třídy.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[SRWLock::LockExclusive – metoda](../windows/srwlock-lockexclusive-method.md)|Získá **SRWLock** objektu ve výhradním režimu.|
|[SRWLock::LockShared – metoda](../windows/srwlock-lockshared-method.md)|Získá **SRWLock** objektu ve sdíleném režimu.|
|[SRWLock::TryLockExclusive – metoda](../windows/srwlock-trylockexclusive-method.md)|Pokusí se získat **srwlock –** objektu ve výhradním režimu pro aktuální nebo zadané **SRWLock** objektu.|
|[SRWLock::TryLockShared – metoda](../windows/srwlock-trylockshared-method.md)|Pokusí se získat **srwlock –** objektu ve sdíleném režimu pro aktuální nebo zadané **SRWLock** objektu.|

### <a name="protected-data-member"></a>Chráněný datový člen

|Název|Popis|
|----------|-----------------|
|[SRWLock::SRWLock_ – datový člen](../windows/srwlock-srwlock-data-member.md)|Obsahuje základní proměnnou zámek pro aktuální **SRWLock** objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SRWLock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)