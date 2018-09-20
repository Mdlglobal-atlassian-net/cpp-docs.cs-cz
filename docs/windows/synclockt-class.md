---
title: Synclockt – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT class
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d557b7ee6e6a0ae627ec7cc9a6b40b5b9dbb872c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379564"
---
# <a name="synclockt-class"></a>SyncLockT – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename SyncTraits
>
class SyncLockT;
```

### <a name="parameters"></a>Parametry

*SyncTraits*<br/>
Typ, který může převzít vlastnictví prostředku.

## <a name="remarks"></a>Poznámky

Představuje typ, který může trvat exkluzivní nebo sdílené vlastnictví prostředku.

**Synclockt –** třída se používá, třeba k implementaci [SRWLock](../windows/srwlock-class.md) třídy.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[SyncLockT::SyncLockT – konstruktor](../windows/synclockt-synclockt-constructor.md)|Inicializuje novou instanci třídy **SyncLockT** třídy.|
|[SyncLockT::~SyncLockT – destruktor](../windows/synclockt-tilde-synclockt-destructor.md)|Uvolní instanci **SyncLockT** třídy.|

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[SyncLockT::SyncLockT – konstruktor](../windows/synclockt-synclockt-constructor.md)|Inicializuje novou instanci třídy **SyncLockT** třídy.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[SyncLockT::IsLocked – metoda](../windows/synclockt-islocked-method.md)|Označuje, zda aktuální **synclockt –** vlastní prostředek objektu; to znamená, **synclockt –** objekt je *uzamčen*.|
|[SyncLockT::Unlock – metoda](../windows/synclockt-unlock-method.md)|Verze ovládacího prvku prostředku držené aktuální **SyncLockT** objektu, pokud existuje.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[SyncLockT::sync_ – datový člen](../windows/synclockt-sync-data-member.md)|Obsahuje základní prostředku reprezentovaného **SyncLockT** třídy.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SyncLockT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers::Details – obor názvů](../windows/microsoft-wrl-wrappers-details-namespace.md)<br/>
[SRWLock – třída](../windows/srwlock-class.md)