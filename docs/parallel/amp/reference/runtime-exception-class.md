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
ms.openlocfilehash: 6ad784720833d2ae5de7d653d132ba144aec2677
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126372"
---
# <a name="runtime_exception-class"></a>runtime_exception – třída

Základní typ pro výjimky v knihovně s C++ akcelerovanou obrovským paralelním zpracováním (amp).

### <a name="syntax"></a>Syntaxe

```cpp
class runtime_exception : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[runtime_exception – konstruktor](#ctor)|Inicializuje novou instanci třídy `runtime_exception`.|
|[~ runtime_exception destruktor](#dtor)|Odstraní objekt `runtime_exception`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get_error_code](#get_error_code)|Vrátí kód chyby, který způsobil výjimku.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného objektu `runtime_exception` do tohoto objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`runtime_exception`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt. h

**Obor názvů:** Concurrency

## <a name="ctor"></a>runtime_exception – konstruktor

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
Hodnota HRESULT chyby, která způsobila výjimku.

*_Other*<br/>
Objekt `runtime_exception` ke zkopírování.

### <a name="return-value"></a>Návratová hodnota

Objekt `runtime_exception`

## <a name="dtor"></a>~ runtime_exception destruktor

Odstraní objekt.

### <a name="syntax"></a>Syntaxe

```cpp
virtual ~runtime_exception() throw();
```

## <a name="get_error_code"></a>get_error_code

Vrátí kód chyby, který způsobil výjimku.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota HRESULT chyby, která způsobila výjimku.

## <a name="operator_eq"></a>operátor =
  Zkopíruje obsah zadaného objektu `runtime_exception` do tohoto objektu.

### <a name="syntax"></a>Syntaxe

```cpp
runtime_exception & operator= (    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt `runtime_exception` ke zkopírování.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento objekt `runtime_exception`.

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
