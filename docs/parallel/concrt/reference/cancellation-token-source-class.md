---
title: cancellation_token_source – třída
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancel
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::create_linked_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::get_token
helpviewer_keywords:
- cancellation_token_source class
ms.assetid: 3548b1a0-12b0-4334-95db-4bf57141c066
ms.openlocfilehash: 330473db1011af661e2cfa2c5861987bce786e40
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296784"
---
# <a name="cancellationtokensource-class"></a>cancellation_token_source – třída

`cancellation_token_source` Třída představuje schopnost zrušit zrušitelnou operaci.

## <a name="syntax"></a>Syntaxe

```
class cancellation_token_source;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[cancellation_token_source](#ctor)|Přetíženo. Sestaví nový `cancellation_token_source`. Zdroj lze použít k nastavení příznaku zrušení některých zrušitelných operací.|
|[~cancellation_token_source Destructor](#dtor)||

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Zrušit](#cancel)|Zruší token. Žádné `task_group`, `structured_task_group`, nebo `task` používající token budou zrušeny při tomto volání a vyvolají výjimku v dalším bodě přerušení.|
|[create_linked_source](#create_linked_source)|Přetíženo. Vytvoří `cancellation_token_source` který se zruší po zrušení poskytnutého tokenu.|
|[get_token](#get_token)|Vrátí token zrušení spojený s tímto zdrojem. Vrácený token lze testovat na zrušení nebo poskytovat zpětné volání, pokud dojde k zrušení.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operátor =](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`cancellation_token_source`

## <a name="requirements"></a>Požadavky

**Záhlaví:** pplcancellation_token.h

**Namespace:** souběžnosti

##  <a name="dtor"></a> ~cancellation_token_source

```
~cancellation_token_source();
```

##  <a name="cancel"></a> Zrušit

Zruší token. Žádné `task_group`, `structured_task_group`, nebo `task` používající token budou zrušeny při tomto volání a vyvolají výjimku v dalším bodě přerušení.

```
void cancel() const;
```

##  <a name="ctor"></a> cancellation_token_source

Sestaví nový `cancellation_token_source`. Zdroj lze použít k nastavení příznaku zrušení některých zrušitelných operací.

```
cancellation_token_source();

cancellation_token_source(const cancellation_token_source& _Src);

cancellation_token_source(cancellation_token_source&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Objekt má zkopírovat nebo přesunout.

##  <a name="create_linked_source"></a> create_linked_source

Vytvoří `cancellation_token_source` který se zruší po zrušení poskytnutého tokenu.

```
static cancellation_token_source create_linked_source(
    cancellation_token& _Src);

template<typename _Iter>
static cancellation_token_source create_linked_source(_Iter _Begin, _Iter _End);
```

### <a name="parameters"></a>Parametry

*_Iter*<br/>
Typ iterátoru.

*_Src*<br/>
Token jehož zrušení bude mít za následek zrušení zdroje vráceného tokenu. Všimněte si, že zdroj vráceného tokenu lze také zrušit nezávisle na zdroji obsaženém v tomto parametru.

*_Zahájit*<br/>
Standardní knihovny C++ iterátor, který odpovídá začátku rozsahu tokenů má naslouchá jejich zrušení.

*_End*<br/>
Standardní knihovny C++ iterátor, který odpovídá konci rozsahu tokenů má naslouchá jejich zrušení.

### <a name="return-value"></a>Návratová hodnota

A `cancellation_token_source` který se zruší po token poskytnutý parametrem `_Src` parametr se zruší.

##  <a name="get_token"></a> get_token

Vrátí token zrušení spojený s tímto zdrojem. Vrácený token lze testovat na zrušení nebo poskytovat zpětné volání, pokud dojde k zrušení.

```
cancellation_token get_token() const;
```

### <a name="return-value"></a>Návratová hodnota

Token zrušení spojený s tímto zdrojem.

##  <a name="operator_neq"></a> Operator! =

```
bool operator!= (const cancellation_token_source& _Src) const;
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Operand.

### <a name="return-value"></a>Návratová hodnota

##  <a name="operator_eq"></a> operátor =

```
cancellation_token_source& operator= (const cancellation_token_source& _Src);

cancellation_token_source& operator= (cancellation_token_source&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Operand.

### <a name="return-value"></a>Návratová hodnota

##  <a name="operator_eq_eq"></a> Operator ==

```
bool operator== (const cancellation_token_source& _Src) const;
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Operand.

### <a name="return-value"></a>Návratová hodnota

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)
