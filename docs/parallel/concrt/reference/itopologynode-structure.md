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
ms.openlocfilehash: 1b4cb6a856d6da7b8eee7f9cba1ad51e375c024d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140062"
---
# <a name="itopologynode-structure"></a>ITopologyNode – struktura

Rozhraní k uzlu topologie, jak je definováno Správce prostředků. Uzel obsahuje jeden nebo více prostředků spuštění.

## <a name="syntax"></a>Syntaxe

```cpp
struct ITopologyNode;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[ITopologyNode:: Getexecutionresourcecount –](#getexecutionresourcecount)|Vrátí počet prostředků spuštění seskupených do tohoto uzlu dohromady.|
|[ITopologyNode:: Getfirstexecutionresource –](#getfirstexecutionresource)|Vrátí první prostředek spuštění seskupený pod tímto uzlem v pořadí výčtu.|
|[ITopologyNode:: getId –](#getid)|Vrátí jedinečný identifikátor Správce prostředků pro tento uzel.|
|[ITopologyNode:: GetNext](#getnext)|Vrátí rozhraní k dalšímu uzlu topologie v pořadí výčtu.|
|[ITopologyNode:: Getnumanode –](#getnumanode)|Vrátí číslo uzlu NUMA přiřazené systémem Windows, ke kterému patří tento uzel Správce prostředku.|

## <a name="remarks"></a>Poznámky

Toto rozhraní se obvykle používá k procházení topologie systému, jak je zjištěno Správce prostředků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ITopologyNode`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm. h

**Obor názvů:** souběžnost

## <a name="getexecutionresourcecount"></a>ITopologyNode:: Getexecutionresourcecount – – metoda

Vrátí počet prostředků spuštění seskupených do tohoto uzlu dohromady.

```cpp
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet prostředků spuštění seskupených do tohoto uzlu dohromady.

## <a name="getfirstexecutionresource"></a>ITopologyNode:: Getfirstexecutionresource – – metoda

Vrátí první prostředek spuštění seskupený pod tímto uzlem v pořadí výčtu.

```cpp
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

První prostředek spuštění seskupený pod tímto uzlem v pořadí výčtu.

## <a name="getid"></a>ITopologyNode:: getId – – metoda

Vrátí jedinečný identifikátor Správce prostředků pro tento uzel.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor Správce prostředků pro tento uzel.

### <a name="remarks"></a>Poznámky

Concurrency Runtime představuje hardwarová vlákna v systému v rámci skupin uzlů procesorů. Uzly jsou obvykle odvozeny od hardwarové topologie systému. Například všechny procesory určitého soketu nebo konkrétního uzlu NUMA mohou patřit do stejného uzlu procesoru. Správce prostředků přiřadí těmto uzlům jedinečné identifikátory počínaje `0` až do `nodeCount - 1`, kde `nodeCount` představuje celkový počet uzlů procesoru v systému.

Počet uzlů lze získat z [GetProcessorNodeCount –](concurrency-namespace-functions.md)funkce.

## <a name="getnext"></a>ITopologyNode:: GetNext – metoda

Vrátí rozhraní k dalšímu uzlu topologie v pořadí výčtu.

```cpp
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Rozhraní k dalšímu uzlu v pořadí výčtu. Pokud v pořadí výčtu systémové topologie nejsou žádné další uzly, vrátí tato metoda hodnotu `NULL`.

## <a name="getnumanode"></a>ITopologyNode:: Getnumanode – – metoda

Vrátí číslo uzlu NUMA přiřazené systémem Windows, ke kterému patří tento uzel Správce prostředku.

```cpp
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Číslo uzlu NUMA přiřazené systémem Windows, ke kterému patří tento uzel Správce prostředků.

### <a name="remarks"></a>Poznámky

Proxy vlákna běžící v kořenovém adresáři virtuálního procesoru patřícím do tohoto uzlu bude mít spřažení na úrovni uzlu NUMA pro uzel NUMA vrácený touto metodou.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
