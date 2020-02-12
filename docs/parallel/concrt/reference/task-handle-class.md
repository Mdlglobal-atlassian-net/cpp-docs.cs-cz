---
title: task_handle – třída
ms.date: 03/27/2019
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
ms.openlocfilehash: a61e72f14448d5033d5be9069ffeec7d3bb08061
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142556"
---
# <a name="task_handle-class"></a>task_handle – třída

Třída `task_handle` představuje jednotlivé paralelní pracovní položky. Tyto pokyny zapouzdřuje a data potřebná ke spuštění nějaké práce.

## <a name="syntax"></a>Syntaxe

```cpp
template<
    typename _Function
>
class task_handle : public ::Concurrency::details::_UnrealizedChore;
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, který bude vyvolán pro provedení práce reprezentované objektem `task_handle`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[task_handle](#task_handle)|Vytvoří nový objekt `task_handle`. Práce úkolu je provedena vyvoláním funkce určené jako parametru konstruktoru.|
|[~ task_handle destruktor](#dtor)|Odstraní objekt `task_handle`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator () – operátor](#task_handle__operator_call)|Operátor volání funkce, který modul runtime vyvolá k provedení práce s popisovačem úlohy.|

## <a name="remarks"></a>Poznámky

`task_handle` objekty lze použít ve spojení s `structured_task_group` nebo obecnější `task_group` objekt pro rozloží práci na paralelní úlohy. Další informace najdete v tématu [Task paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Všimněte si, že tvůrce objektu `task_handle` zodpovídá za zachování životnosti vytvořeného `task_handle` objektu, dokud jej Concurrency Runtime nepožaduje. Obvykle to znamená, že objekt `task_handle` nesmí destrukci, dokud není volána metoda `wait` nebo `run_and_wait` `task_group` nebo `structured_task_group`, na kterou je zařazena do fronty.

`task_handle` objekty se obvykle používají ve spojení s C++ výrazy lambda. Vzhledem k tomu, že neznáte skutečný typ výrazu lambda, funkce [make_task](concurrency-namespace-functions.md#make_task) se obvykle používá k vytvoření objektu `task_handle`.

Modul runtime vytvoří kopii pracovní funkce, kterou předáte objektu `task_handle`. Proto všechny změny stavu, ke kterým dojde v objektu funkce, který předáte objektu `task_handle`, se nezobrazí ve vaší kopii objektu funkce.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`task_handle`

## <a name="requirements"></a>Požadavky

**Záhlaví:** PPL. h

**Obor názvů:** souběžnost

## <a name="task_handle__operator_call"></a>operator () – operátor

Operátor volání funkce, který modul runtime vyvolá k provedení práce s popisovačem úlohy.

```cpp
void operator()() const;
```

## <a name="task_handle"></a>task_handle

Vytvoří nový objekt `task_handle`. Práce úkolu je provedena vyvoláním funkce určené jako parametru konstruktoru.

```cpp
task_handle(const _Function& _Func);
```

### <a name="parameters"></a>Parametry

*_Func*<br/>
Funkce, která bude vyvolána pro provedení práce reprezentované objektem `task_handle`. Může to být lambda funktor, ukazatel na funkci nebo libovolný objekt, který podporuje verzi operátoru volání funkce s podpisem `void operator()()`.

### <a name="remarks"></a>Poznámky

Modul runtime vytvoří kopii pracovní funkce, kterou předáte konstruktoru. Proto všechny změny stavu, ke kterým dojde v objektu funkce, který předáte objektu `task_handle`, se nezobrazí ve vaší kopii objektu funkce.

## <a name="dtor"></a>~ task_handle

Odstraní objekt `task_handle`.

```cpp
~task_handle();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[task_group – třída](task-group-class.md)<br/>
[structured_task_group – třída](structured-task-group-class.md)
