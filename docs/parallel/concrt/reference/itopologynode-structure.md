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
ms.openlocfilehash: 867e0543d1b9f2810a3fe761f038947c4d88da4d
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346225"
---
# <a name="itopologynode-structure"></a>ITopologyNode – struktura

Rozhraní pro uzel topologie definované správcem prostředků. Uzel obsahuje jeden nebo více spuštění prostředků.

## <a name="syntax"></a>Syntaxe

```
struct ITopologyNode;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[ITopologyNode::GetExecutionResourceCount](#getexecutionresourcecount)|Vrátí počet spuštění prostředků seskupí dohromady pod tímto uzlem.|
|[ITopologyNode::GetFirstExecutionResource](#getfirstexecutionresource)|Vrátí první spuštění prostředků seskupené pod tento uzel v pořadí výčtu.|
|[Itopologynode::getid –](#getid)|Vrátí jedinečný identifikátor správce prostředků pro tento uzel.|
|[Itopologynode::GetNext –](#getnext)|Vrátí rozhraní k dalšímu uzlu topologie v pořadí výčtu.|
|[ITopologyNode::GetNumaNode](#getnumanode)|Číslo uzlu NUMA, ke kterému patří tento uzel zdrojů systémem přiřazené vrátí Windows.|

## <a name="remarks"></a>Poznámky

Toto rozhraní se obvykle používá pro vás topologii tohoto systému, jak pomocí Správce prostředků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ITopologyNode`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Namespace:** souběžnosti

##  <a name="getexecutionresourcecount"></a>  Itopologynode::getexecutionresourcecount – metoda

Vrátí počet spuštění prostředků seskupí dohromady pod tímto uzlem.

```
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet spuštění prostředků seskupí dohromady pod tímto uzlem.

##  <a name="getfirstexecutionresource"></a>  Itopologynode::getfirstexecutionresource – metoda

Vrátí první spuštění prostředků seskupené pod tento uzel v pořadí výčtu.

```
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Na první prostředek provádění seskupené pod tento uzel v pořadí výčtu.

##  <a name="getid"></a>  Itopologynode::getid – metoda

Vrátí jedinečný identifikátor správce prostředků pro tento uzel.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Správce prostředků jedinečný identifikátor pro tento uzel.

### <a name="remarks"></a>Poznámky

Modul Concurrency Runtime představuje hardwarových vláken v systému ve skupinách procesoru uzlů. Uzly jsou obvykle odvozena z hardwarovou topologii systému. Všechny procesory na soket zvláštní nebo konkrétní uzel NUMA může například patřit do stejného uzlu procesoru. Resource Manager přiřadí tyto uzly počínaje jedinečné identifikátory `0` včetně `nodeCount - 1`, kde `nodeCount` představuje celkový počet uzlů procesoru v systému.

Počet uzlů, které se získají z funkce [getprocessornodecount –](concurrency-namespace-functions.md).

##  <a name="getnext"></a>  Itopologynode::GetNext – metoda

Vrátí rozhraní k dalšímu uzlu topologie v pořadí výčtu.

```
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Rozhraní pro další uzel v pořadí výčtu. Pokud v pořadí výčtu topologie systému nejsou žádné další uzly, tato metoda vrátí hodnotu `NULL`.

##  <a name="getnumanode"></a>  Itopologynode::getnumanode – metoda

Číslo uzlu NUMA, ke kterému patří tento uzel zdrojů systémem přiřazené vrátí Windows.

```
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Číslo uzlu NUMA, ke kterému patří tento uzel správce prostředků přiřazené Windows.

### <a name="remarks"></a>Poznámky

Proxy vlákno spuštěné na kořenovém virtuálním procesoru patřícím do tohoto uzlu bude mít příbuznost alespoň na úrovni uzlu NUMA pro uzel NUMA vrácený touto metodou.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)
