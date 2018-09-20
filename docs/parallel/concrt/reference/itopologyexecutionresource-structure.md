---
title: Itopologyexecutionresource – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
dev_langs:
- C++
helpviewer_keywords:
- ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60a0097aded73e3e0251d38daf5da71197668d3a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383789"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource – struktura

Rozhraní pro prostředek provádění definované správcem prostředků.

## <a name="syntax"></a>Syntaxe

```
struct ITopologyExecutionResource;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Itopologyexecutionresource::getid –](#getid)|Vrátí jedinečný identifikátor správce prostředků pro tento prostředek spuštění.|
|[Itopologyexecutionresource::GetNext –](#getnext)|Vrátí rozhraní pro další spuštění prostředku v pořadí výčtu.|

## <a name="remarks"></a>Poznámky

Toto rozhraní se obvykle používá pro vás topologii tohoto systému, jak pomocí Správce prostředků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ITopologyExecutionResource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Namespace:** souběžnosti

##  <a name="getid"></a>  Itopologyexecutionresource::getid – metoda

Vrátí jedinečný identifikátor správce prostředků pro tento prostředek spuštění.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Správce prostředků jedinečný identifikátor pro tento prostředek spuštění.

##  <a name="getnext"></a>  Itopologyexecutionresource::GetNext – metoda

Vrátí rozhraní pro další spuštění prostředku v pořadí výčtu.

```
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Rozhraní pro další spuštění prostředku v pořadí výčtu. Pokud v pořadí výčtu uzlu, ke kterému patří tento prostředek spuštění nejsou žádné další uzly, tato metoda vrátí hodnotu `NULL`.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
