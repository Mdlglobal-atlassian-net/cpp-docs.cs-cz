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
ms.openlocfilehash: 2c9221cab1ac2d48bd099a769188e4bee797823c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368151"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource – struktura

Rozhraní k prostředku spuštění, jak je definováno Správcem prostředků.

## <a name="syntax"></a>Syntaxe

```cpp
struct ITopologyExecutionResource;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[ITopologyExecutionResource::GetId](#getid)|Vrátí jedinečný identifikátor správce prostředků pro tento prostředek spuštění.|
|[ITopologyExecutionResource::GetNext](#getnext)|Vrátí rozhraní další prostředek spuštění v pořadí výčtu.|

## <a name="remarks"></a>Poznámky

Toto rozhraní se obvykle používá k procházce topologie systému, jak je pozorováno správce prostředků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ITopologyExecutionResource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Obor názvů:** souběžnost

## <a name="itopologyexecutionresourcegetid-method"></a><a name="getid"></a>ITopologyExecutionResource::Metoda GetId

Vrátí jedinečný identifikátor správce prostředků pro tento prostředek spuštění.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor správce prostředků pro tento prostředek spuštění.

## <a name="itopologyexecutionresourcegetnext-method"></a><a name="getnext"></a>ITopologyExecutionResource::GetNext Metoda

Vrátí rozhraní další prostředek spuštění v pořadí výčtu.

```cpp
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Rozhraní k dalšímu prostředku spuštění v pořadí výčtu. Pokud neexistují žádné další uzly v pořadí výčtu uzlu, do kterého patří `NULL`tento prostředek spuštění, tato metoda vrátí hodnotu .

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)
