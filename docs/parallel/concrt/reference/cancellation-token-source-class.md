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
ms.openlocfilehash: 131c4155ad902221d14f90f750f89c31479e2067
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142233"
---
# <a name="cancellation_token_source-class"></a>cancellation_token_source – třída

Třída `cancellation_token_source` představuje schopnost zrušit některé operace, které lze zrušit.

## <a name="syntax"></a>Syntaxe

```cpp
class cancellation_token_source;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[cancellation_token_source](#ctor)|Přetíženo. Vytvoří nový `cancellation_token_source`. Zdroj lze použít k označení zrušení některých operací, které lze zrušit.|
|[~ cancellation_token_source destruktor](#dtor)||

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[operaci](#cancel)|Zruší token. Jakékoli `task_group`, `structured_task_group`nebo `task`, které využívají token, se po tomto volání zruší a vyvolají výjimku v dalším bodu přerušení.|
|[create_linked_source](#create_linked_source)|Přetíženo. Vytvoří `cancellation_token_source`, který se zruší při zrušení poskytnutého tokenu.|
|[get_token](#get_token)|Vrátí token zrušení přidružený k tomuto zdroji. Vrácený token lze dotazovat na zrušení nebo poskytnout zpětné volání, pokud dojde k zrušení.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operátor =](#operator_eq)||
|[operator = = – operátor](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`cancellation_token_source`

## <a name="requirements"></a>Požadavky

**Záhlaví:** pplcancellation_token. h

**Obor názvů:** souběžnost

## <a name="dtor"></a>~ cancellation_token_source

```cpp
~cancellation_token_source();
```

## <a name="cancel"></a>operaci

Zruší token. Jakékoli `task_group`, `structured_task_group`nebo `task`, které využívají token, se po tomto volání zruší a vyvolají výjimku v dalším bodu přerušení.

```cpp
void cancel() const;
```

## <a name="ctor"></a>cancellation_token_source

Vytvoří nový `cancellation_token_source`. Zdroj lze použít k označení zrušení některých operací, které lze zrušit.

```cpp
cancellation_token_source();

cancellation_token_source(const cancellation_token_source& _Src);

cancellation_token_source(cancellation_token_source&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Objekt, který se má zkopírovat nebo přesunout.

## <a name="create_linked_source"></a>create_linked_source

Vytvoří `cancellation_token_source`, který se zruší při zrušení poskytnutého tokenu.

```cpp
static cancellation_token_source create_linked_source(
    cancellation_token& _Src);

template<typename _Iter>
static cancellation_token_source create_linked_source(_Iter _Begin, _Iter _End);
```

### <a name="parameters"></a>Parametry

*_Iter*<br/>
Typ iterátoru

*_Src*<br/>
Token, jehož zrušení způsobí zrušení vráceného zdroje tokenu. Všimněte si, že vrácený zdroj tokenu lze také zrušit nezávisle na zdroji obsaženém v tomto parametru.

*_Begin*<br/>
C++ Standardní knihovna iterátoru odpovídající začátku rozsahu tokenů, aby naslouchala zrušení.

*_End*<br/>
C++ Standardní knihovna iterátoru odpovídající konci rozsahu tokenů, aby naslouchala zrušení.

### <a name="return-value"></a>Návratová hodnota

`cancellation_token_source`, který je zrušen, pokud je token poskytnutý parametrem `_Src` zrušen.

## <a name="get_token"></a>get_token

Vrátí token zrušení přidružený k tomuto zdroji. Vrácený token lze dotazovat na zrušení nebo poskytnout zpětné volání, pokud dojde k zrušení.

```cpp
cancellation_token get_token() const;
```

### <a name="return-value"></a>Návratová hodnota

Token zrušení spojený s tímto zdrojem.

## <a name="operator_neq"></a>! = – operátor

```cpp
bool operator!= (const cancellation_token_source& _Src) const;
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Pravý.

### <a name="return-value"></a>Návratová hodnota

## <a name="operator_eq"></a>operátor =

```cpp
cancellation_token_source& operator= (const cancellation_token_source& _Src);

cancellation_token_source& operator= (cancellation_token_source&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Pravý.

### <a name="return-value"></a>Návratová hodnota

## <a name="operator_eq_eq"></a>operator = = – operátor

```cpp
bool operator== (const cancellation_token_source& _Src) const;
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Pravý.

### <a name="return-value"></a>Návratová hodnota

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
