---
title: ITopologyExecutionResource – struktura
ms.date: 11/04/2016
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
helpviewer_keywords:
- ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
ms.openlocfilehash: 4bfb614d5ffd6a399fae33d38a50cee62f17c208
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64339493"
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

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)
