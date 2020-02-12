---
title: combinable – třída
ms.date: 11/04/2016
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
ms.openlocfilehash: a1954cd3a69233deed053da5b5fdef0dbc183b80
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141435"
---
# <a name="combinable-class"></a>combinable – třída

Objekt `combinable<T>` je určen k poskytování kopií dat v soukromém vlákně, aby bylo možné provádět místní výpočty bez omezení na více vláken během paralelních algoritmů. Na konci paralelní operace mohou být dílčí výpočty privátních vláken sloučeny do konečného výsledku. Tato třída se dá použít místo sdílené proměnné a může mít za následek zlepšení výkonu, pokud by se v této sdílené proměnné mohlo nacházet hodně sporů.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
class combinable;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Datový typ finálního sloučeného výsledku. Typ musí mít kopírovací konstruktor a výchozí konstruktor.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[combinable](#ctor)|Přetíženo. Vytvoří nový objekt `combinable`.|
|[~ kombinace destruktoru](#dtor)|Odstraní objekt `combinable`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[jejich](#clear)|Vymaže všechny mezilehlé výsledky výpočtů z předchozího použití.|
|[spojen](#combine)|Vypočítá konečnou hodnotu ze sady dílčích výpočtů místních vláken voláním poskytnuté kombinace funktor.|
|[combine_each](#combine_each)|Vypočítá konečnou hodnotu ze sady dílčích výpočtů místních vláken voláním dodané kombinace funktor jednou pro místní dílčí výpočet vlákna. Konečný výsledek je shromážděn objektem funkce.|
|[local](#local)|Přetíženo. Vrátí odkaz na podprocesově privátní výpočet.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Přiřadí objekt `combinable` z jiného objektu `combinable`.|

## <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [Parallel Containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`combinable`

## <a name="requirements"></a>Požadavky

**Záhlaví:** PPL. h

**Obor názvů:** souběžnost

## <a name="clear"></a>jejich

Vymaže všechny mezilehlé výsledky výpočtů z předchozího použití.

```cpp
void clear();
```

## <a name="ctor"></a>combinable

Vytvoří nový objekt `combinable`.

```cpp
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ inicializačního objektu funktor

*_FnInitialize*<br/>
Funkce, která bude volána pro inicializaci každé nové soukromé hodnoty pro vlákno typu `T`. Musí podporovat operátor volání funkce s podpisem `T ()`.

*_Copy*<br/>
Existující objekt `combinable`, který se má zkopírovat do tohoto objektu.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje nové prvky s výchozím konstruktorem pro typ `T`.

Druhý konstruktor inicializuje nové prvky pomocí inicializačního funktor zadaného jako parametr `_FnInitialize`.

Třetí konstruktor je kopírovací konstruktor.

## <a name="dtor"></a>~ kombinace

Odstraní objekt `combinable`.

```cpp
~combinable();
```

## <a name="combine"></a>spojen

Vypočítá konečnou hodnotu ze sady dílčích výpočtů místních vláken voláním poskytnuté kombinace funktor.

```cpp
template<typename _Function>
T combine(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, který bude vyvolán pro kombinování dvou dílčích výpočtů místních vláken.

*_FnCombine*<br/>
Funktor, který se používá ke kombinování dílčích výpočtů. Jeho podpis je `T (T, T)` nebo `T (const T&, const T&)`a musí být asociativní a komutativní.

### <a name="return-value"></a>Návratová hodnota

Konečný výsledek kombinace všech dílčích výpočtů privátních vláken.

## <a name="combine_each"></a>combine_each

Vypočítá konečnou hodnotu ze sady dílčích výpočtů místních vláken voláním dodané kombinace funktor jednou pro místní dílčí výpočet vlákna. Konečný výsledek je shromážděn objektem funkce.

```cpp
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, který bude vyvolán pro kombinování jednoho dílčího výpočtu místního vlákna.

*_FnCombine*<br/>
Funktor, který slouží ke kombinování jednoho dílčího výpočtu. Jeho signatura je `void (T)` nebo `void (const T&)`a musí být asociativní a komutativní.

## <a name="local"></a>místní

Vrátí odkaz na podprocesově privátní výpočet.

```cpp
T& local();

T& local(bool& _Exists);
```

### <a name="parameters"></a>Parametry

*_Exists*<br/>
Odkaz na logickou hodnotu. Logická hodnota, na kterou je odkazováno pomocí tohoto argumentu, bude nastavena na **hodnotu true** , pokud dílčí výpočet již existoval v tomto vlákně, a nastavte na **hodnotu false** , pokud se jednalo o první dílčí výpočet v tomto vlákně.

### <a name="return-value"></a>Návratová hodnota

Odkaz na dílčí výpočet privátního vlákna.

## <a name="operator_eq"></a>operátor =

Přiřadí objekt `combinable` z jiného objektu `combinable`.

```cpp
combinable& operator= (const combinable& _Copy);
```

### <a name="parameters"></a>Parametry

*_Copy*<br/>
Existující objekt `combinable`, který se má zkopírovat do tohoto objektu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento objekt `combinable`.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
