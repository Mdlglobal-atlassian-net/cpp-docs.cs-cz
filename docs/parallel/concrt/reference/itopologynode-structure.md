---
title: ITopologyNode – struktura
ms.date: 11/04/2016
f1_keywords:
- ITopologyNode
- CONCRTRM/concurrency::ITopologyNode
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetExecutionResourceCount
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetFirstExecutionResource
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetId
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNext
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNumaNode
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
ms.openlocfilehash: 7cb815c4f7dc5ad09e8d352abc3f3375b8d9e205
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368108"
---
# <a name="itopologynode-structure"></a>ITopologyNode – struktura

Rozhraní k toplogickému uzlu definovanému Správcem prostředků. Uzel obsahuje jeden nebo více prostředků spuštění.

## <a name="syntax"></a>Syntaxe

```cpp
struct ITopologyNode;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[ITopologyNode::GetExecutionResourceCount](#getexecutionresourcecount)|Vrátí počet prostředků spuštění seskupených v rámci tohoto uzlu.|
|[ITopologyNode::GetFirstExecutionResource](#getfirstexecutionresource)|Vrátí první prostředek spuštění seskupený pod tímto uzlem v pořadí výčtu.|
|[ITopologyNode::GetId](#getid)|Vrátí jedinečný identifikátor správce prostředků pro tento uzel.|
|[ITopologyNode::GetNext](#getnext)|Vrátí rozhraní do dalšího uzlu topologie v pořadí výčtu.|
|[ITopologyNode::GetNumaNode](#getnumanode)|Vrátí číslo uzlu NUMA přiřazeného systémem Windows, ke kterému tento uzel Maanger prostředků patří.|

## <a name="remarks"></a>Poznámky

Toto rozhraní se obvykle používá k procházce topologie systému, jak je pozorováno správce prostředků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ITopologyNode`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Obor názvů:** souběžnost

## <a name="itopologynodegetexecutionresourcecount-method"></a><a name="getexecutionresourcecount"></a>ITopologyNode::Metoda GetExecutionResourceCount

Vrátí počet prostředků spuštění seskupených v rámci tohoto uzlu.

```cpp
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet prostředků spuštění seskupených pod tímto uzlem.

## <a name="itopologynodegetfirstexecutionresource-method"></a><a name="getfirstexecutionresource"></a>ITopologyNode::Metoda GetFirstExecutionResource

Vrátí první prostředek spuštění seskupený pod tímto uzlem v pořadí výčtu.

```cpp
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

První prostředek spuštění seskupený pod tímto uzlem v pořadí výčtu.

## <a name="itopologynodegetid-method"></a><a name="getid"></a>ITopologyNode::GetId Metoda

Vrátí jedinečný identifikátor správce prostředků pro tento uzel.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor správce prostředků pro tento uzel.

### <a name="remarks"></a>Poznámky

Modul Souběžnost Runtime představuje hardwarová vlákna v systému ve skupinách uzlů procesoru. Uzly jsou obvykle odvozeny z hardwarové topologie systému. Například všechny procesory na určitém soketu nebo konkrétní uzel NUMA může patřit do stejného uzlu procesoru. Správce prostředků přiřazuje těmto uzlům jedinečné identifikátory počínaje `0` až do a včetně `nodeCount - 1`, kde `nodeCount` představuje celkový počet uzlů procesoru v systému.

Počet uzlů lze získat z funkce [GetProcessorNodeCount](concurrency-namespace-functions.md).

## <a name="itopologynodegetnext-method"></a><a name="getnext"></a>ITopologyNode::GetNext Metoda

Vrátí rozhraní do dalšího uzlu topologie v pořadí výčtu.

```cpp
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Rozhraní k dalšímu uzlu v pořadí výčtu. Pokud nejsou žádné další uzly v pořadí výčtu topologie systému, tato metoda vrátí hodnotu `NULL`.

## <a name="itopologynodegetnumanode-method"></a><a name="getnumanode"></a>ITopologyNode::Metoda GetNumaNode

Vrátí číslo uzlu NUMA přiřazeného systémem Windows, ke kterému tento uzel Maanger prostředků patří.

```cpp
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Číslo uzlu NUMA přiřazené systémem Windows, ke kterému tento uzel Správce prostředků patří.

### <a name="remarks"></a>Poznámky

Proxy podproces spuštěný na kořenovém adresáři virtuálního procesoru, který patří k tomuto uzlu, bude mít spřažení alespoň s úrovní uzlu NUMA pro uzel NUMA vrácený touto metodou.

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)
