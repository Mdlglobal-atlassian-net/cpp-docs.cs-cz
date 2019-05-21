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
ms.openlocfilehash: 8ed3fb5edd861eaecd0bf9a39687a2a63fdfe695
ms.sourcegitcommit: a61d17cffdd50f1c3c6e082a01bbcbc85b6cc5a7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975184"
---
# <a name="runtimeexception-class"></a>runtime_exception – třída

Základní typ výjimky v knihovně C++ Accelerated Massive Parallelism (AMP).

### <a name="syntax"></a>Syntaxe

```
class runtime_exception : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[runtime_exception Constructor](#ctor)|Inicializuje novou instanci třídy `runtime_exception` třídy.|
|[~runtime_exception Destructor](#dtor)|Odstraní `runtime_exception` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[get_error_code](#get_error_code)|Vrátí kód chyby, který způsobil výjimku.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `runtime_exception` do tohoto objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`runtime_exception`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt.h

**Namespace:** Souběžnost

## <a name="ctor"></a>  runtime_exception – konstruktor

Inicializuje novou instanci třídy.

### <a name="syntax"></a>Syntaxe

```
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

*Ji_né*<br/>
`runtime_exception` Objektu, který chcete zkopírovat.

### <a name="return-value"></a>Návratová hodnota

`runtime_exception` Objektu.

## <a name="dtor"></a>  ~ runtime_exception – destruktor

Odstraní objekt.

### <a name="syntax"></a>Syntaxe

```
virtual ~runtime_exception() throw();
```

## <a name="get_error_code"></a> get_error_code

Vrátí kód chyby, který způsobil výjimku.

### <a name="syntax"></a>Syntaxe

```
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota HRESULT chyby, která způsobila výjimku.

## <a name="operator_eq"></a>  operátor =
  Zkopíruje obsah zadaného `runtime_exception` do tohoto objektu.

### <a name="syntax"></a>Syntaxe

```
runtime_exception & operator= (    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`runtime_exception` Objektu, který chcete zkopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `runtime_exception` objektu.

## <a name="see-also"></a>Viz také:

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
