---
title: Synclockwithstatust – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT class
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 69676651c77175b55f4363b525a3ca3acb9be46d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437453"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename SyncTraits
>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Parametry

*SyncTraits*<br/>
Typ, který může trvat exkluzivní nebo sdílené vlastnictví prostředku.

## <a name="remarks"></a>Poznámky

Představuje typ, který může trvat exkluzivní nebo sdílené vlastnictví prostředku.

**Synclockwithstatust –** třída se používá k implementaci [Mutex](../windows/mutex-class1.md) a [semafor](../windows/semaphore-class.md) třídy.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[SyncLockWithStatusT::SyncLockWithStatusT – konstruktor](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Inicializuje novou instanci třídy **synclockwithstatust –** třídy.|

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[SyncLockWithStatusT::SyncLockWithStatusT – konstruktor](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Inicializuje novou instanci třídy **synclockwithstatust –** třídy.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[SyncLockWithStatusT::GetStatus – metoda](../windows/synclockwithstatust-getstatus-method.md)|Načte aktuální stav Čekání **synclockwithstatust –** objektu.|
|[SyncLockWithStatusT::IsLocked – metoda](../windows/synclockwithstatust-islocked-method.md)|Označuje, zda aktuální **synclockwithstatust –** vlastní prostředek objektu; to znamená, **synclockwithstatust –** objekt je *uzamčen*.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[SyncLockWithStatusT::status_ – datový člen](../windows/synclockwithstatust-status-data-member.md)|Obsahuje výsledek základní operace čekání po operaci zámku na objektu na základě aktuálního **synclockwithstatust –** objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers::Details – obor názvů](../windows/microsoft-wrl-wrappers-details-namespace.md)