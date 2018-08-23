---
title: Mutex – Třída1 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex class
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b20c270f7848a346d717357f474d89e37ea117a4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600025"
---
# <a name="mutex-class1"></a>Mutex – Třída1

Představuje objekt synchronizace, který řídí výhradně sdíleného prostředku.

## <a name="syntax"></a>Syntaxe

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`SyncLock`|Synonymum pro třídu, která podporuje synchronní zámky.|

### <a name="public-constructor"></a>Veřejný konstruktor

|Název|Popis|
|----------|-----------------|
|[Mutex::Mutex – konstruktor](../windows/mutex-mutex-constructor.md)|Inicializuje novou instanci třídy **Mutex** třídy.|

### <a name="public-members"></a>Veřejné členy

|Název|Popis|
|----------|-----------------|
|[Mutex::Lock – metoda](../windows/mutex-lock-method.md)|Počká, až do aktuálního objektu nebo **Mutex** objekt přidružený k Zadaný popisovač mutex nebo zadaný časový limit uplynul vydané verze.|

### <a name="public-operator"></a>Veřejný operátor

|Název|Popis|
|----------|-----------------|
|[Mutex::operator= – operátor](../windows/mutex-operator-assign-operator.md)|Přiřadí (přesun) zadaný **Mutex** objektů na aktuální **Mutex** objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Mutex`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)