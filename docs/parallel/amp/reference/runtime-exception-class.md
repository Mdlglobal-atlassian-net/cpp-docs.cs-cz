---
title: runtime_exception – třída
ms.date: 03/27/2019
f1_keywords:
- runtime_exception
- AMPRT/runtime_exception
- AMPRT/Concurrency::runtime_exception
- AMPRT/Concurrency::runtime_exception::get_error_code
helpviewer_keywords:
- runtime_exception class
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
ms.openlocfilehash: ff54357055d373db98f469b071edc75fce75e0b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336800"
---
# <a name="runtime_exception-class"></a>runtime_exception – třída

Základní typ pro výjimky v knihovně C++ Accelerated Massive Parallelism (AMP).

### <a name="syntax"></a>Syntaxe

```cpp
class runtime_exception : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[konstruktor runtime_exception](#ctor)|Inicializuje novou instanci třídy. `runtime_exception`|
|[~runtime_exception Destruktor](#dtor)|Zničí `runtime_exception` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[get_error_code](#get_error_code)|Vrátí kód chyby, která způsobila výjimku.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `runtime_exception` objektu do tohoto objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`runtime_exception`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt.h

**Obor názvů:** Souběžnost

## <a name="runtime_exception-constructor"></a><a name="ctor"></a>konstruktor runtime_exception

Inicializuje novou instanci třídy.

### <a name="syntax"></a>Syntaxe

```cpp
runtime_exception(
    const char * _Message,
    HRESULT _Hresult ) throw();

explicit runtime_exception(
    HRESULT _Hresult ) throw();

runtime_exception(
    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popis chyby, která způsobila výjimku.

*_Hresult*<br/>
HRESULT chyby, která způsobila výjimku.

*_Other*<br/>
Objekt, `runtime_exception` který chcete zkopírovat.

### <a name="return-value"></a>Návratová hodnota

Objekt `runtime_exception`

## <a name="runtime_exception-destructor"></a><a name="dtor"></a>~runtime_exception Destruktor

Zničí objekt.

### <a name="syntax"></a>Syntaxe

```cpp
virtual ~runtime_exception() throw();
```

## <a name="get_error_code"></a><a name="get_error_code"></a>get_error_code

Vrátí kód chyby, která způsobila výjimku.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Návratová hodnota

HRESULT chyby, která způsobila výjimku.

## <a name="operator"></a><a name="operator_eq"></a>operátor =

Zkopíruje obsah zadaného `runtime_exception` objektu do tohoto objektu.

### <a name="syntax"></a>Syntaxe

```cpp
runtime_exception & operator= (    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt, `runtime_exception` který chcete zkopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na `runtime_exception` tento objekt.

## <a name="see-also"></a>Viz také

[Obor názvů souběžnosti (C++ AMP)](concurrency-namespace-cpp-amp.md)
