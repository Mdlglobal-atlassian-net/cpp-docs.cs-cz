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
ms.openlocfilehash: 82193a9b592cded96f3726cbabd6cf646eaa27c8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140071"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource – struktura

Rozhraní k prostředku spuštění, jak je definováno Správce prostředků.

## <a name="syntax"></a>Syntaxe

```cpp
struct ITopologyExecutionResource;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Itopologyexecutionresource –:: getId –](#getid)|Vrátí jedinečný identifikátor Správce prostředků pro tento prostředek spuštění.|
|[Itopologyexecutionresource –:: GetNext](#getnext)|Vrátí rozhraní k dalšímu prostředku spuštění v pořadí výčtu.|

## <a name="remarks"></a>Poznámky

Toto rozhraní se obvykle používá k procházení topologie systému, jak je zjištěno Správce prostředků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ITopologyExecutionResource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm. h

**Obor názvů:** souběžnost

## <a name="getid"></a>Itopologyexecutionresource –:: getId – – metoda

Vrátí jedinečný identifikátor Správce prostředků pro tento prostředek spuštění.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor Správce prostředků pro tento prostředek spuštění.

## <a name="getnext"></a>Itopologyexecutionresource –:: GetNext – metoda

Vrátí rozhraní k dalšímu prostředku spuštění v pořadí výčtu.

```cpp
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Rozhraní k dalšímu prostředku spuštění v pořadí výčtu. Pokud neexistují žádné další uzly v pořadí výčtu uzlu, ke kterému patří tento prostředek spuštění, vrátí tato metoda hodnotu `NULL`.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
