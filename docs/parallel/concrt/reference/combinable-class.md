---
title: combinable – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
dev_langs:
- C++
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d544ac392e2eb227d7e1c37412110d09272f10d5
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162502"
---
# <a name="combinable-class"></a>combinable – třída

`combinable<T>` Objektu je určená k zajištění vlákno soukromé kopie dat, provádět výpočty bez zámku thread local dílčí během paralelních algoritmů. Na konci paralelní operace můžete vlákno privátní dílčí výpočty pak sloučen do konečný výsledek. Tato třída je možné použít místo sdílené proměnné a může vést k zlepšení výkonu, pokud by jinak byly velké množství kolizí v dané sdílené proměnné.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class combinable;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ konečný výsledek sloučení. Typ musí mít konstruktor kopie a výchozí konstruktor.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[combinable –](#ctor)|Přetíženo. Sestaví nový `combinable` objektu.|
|[~ combinable – destruktor](#dtor)|Odstraní `combinable` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Vymazat](#clear)|Vymaže všechny výpočetní mezivýsledků z předchozí spotřeby.|
|[kombinování](#combine)|Vypočítá konečnou hodnotu ze sady dílčích výpočty místního vlákna voláním Zadaná kombinace funktor.|
|[combine_each](#combine_each)|Vypočítá konečnou hodnotu ze sady dílčích výpočty místního vlákna voláním funktor Zadaná kombinace jednou za dílčí výpočtu místního vlákna. Konečný výsledek je shromážděných řešením objektu funkce.|
|[local](#local)|Přetíženo. Vrátí odkaz na dílčí výpočtu privátní vlákna.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Přiřadí `combinable` objektu z jiného `combinable` objektu.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`combinable`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppl.h

**Namespace:** souběžnosti

##  <a name="clear"></a> Vymazat

Vymaže všechny výpočetní mezivýsledků z předchozí spotřeby.

```
void clear();
```

##  <a name="ctor"></a> combinable –

Sestaví nový `combinable` objektu.

```
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu inicializace funktor.

*_FnInitialize*<br/>
Funkce, která bude volána k inicializaci každé nové vlákno privátní hodnotu typu `T`. Operátor volání funkce s podpisem musí podporovat `T ()`.

*_Kopírovat*<br/>
Existující `combinable` objektu, které se mají zkopírovat do tohoto objektu.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje nové prvky s výchozí konstruktor pro typ `T`.

Druhý konstruktor inicializuje nové prvky pomocí inicializace funktor zadaný jako `_FnInitialize` parametru.

Třetí konstruktor je kopírovací konstruktor.

##  <a name="dtor"></a> ~ combinable –

Odstraní `combinable` objektu.

```
~combinable();
```

##  <a name="combine"></a> kombinování

Vypočítá konečnou hodnotu ze sady dílčích výpočty místního vlákna voláním Zadaná kombinace funktor.

```
template<typename _Function>
T combine(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, která bude volána ke sloučení dvou dílčích výpočty místního vlákna.

*_FnCombine*<br/>
Funktor, který se používá ke sloučení dílčí výpočty. Jeho podpis je `T (T, T)` nebo `T (const T&, const T&)`, a musí být asociativních a komutativní.

### <a name="return-value"></a>Návratová hodnota

Konečný výsledek kombinace všechny dílčí výpočty privátní vlákna.

##  <a name="combine_each"></a> combine_each –

Vypočítá konečnou hodnotu ze sady dílčích výpočty místního vlákna voláním funktor Zadaná kombinace jednou za dílčí výpočtu místního vlákna. Konečný výsledek je shromážděných řešením objektu funkce.

```
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, která bude vyvolána zkombinovat jeden dílčí výpočtu místního vlákna.

*_FnCombine*<br/>
Funktor, který se používá ke sloučení jeden dílčí výpočtu. Jeho podpis je `void (T)` nebo `void (const T&)`a musí být asociativní a komutativní.

##  <a name="local"></a> místní

Vrátí odkaz na dílčí výpočtu privátní vlákna.

```
T& local();

T& local(bool& _Exists);
```

### <a name="parameters"></a>Parametry

*_Exists*<br/>
Odkaz na logickou hodnotu. Logická hodnota, odkazuje tento argument se nastaví **true** Pokud dílčí výpočtu již existoval v tomto vláknu a nastavte na **false** Pokud jste to byli první dílčí výpočet v tomto vlákně.

### <a name="return-value"></a>Návratová hodnota

Odkaz na dílčí výpočtu privátní vlákna.

##  <a name="operator_eq"></a> operátor =

Přiřadí `combinable` objektu z jiného `combinable` objektu.

```
combinable& operator= (const combinable& _Copy);
```

### <a name="parameters"></a>Parametry

*_Kopírovat*<br/>
Existující `combinable` objektu, které se mají zkopírovat do tohoto objektu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `combinable` objektu.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
