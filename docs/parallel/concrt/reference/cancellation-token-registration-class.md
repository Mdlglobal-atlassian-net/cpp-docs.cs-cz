---
title: cancellation_token_registration – třída
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration::cancellation_token_registration
helpviewer_keywords:
- cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
ms.openlocfilehash: 9342841e207c93b66521c2fc742c1b1114682f78
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142241"
---
# <a name="cancellation_token_registration-class"></a>cancellation_token_registration – třída

Třída `cancellation_token_registration` představuje oznámení zpětného volání z `cancellation_token`. Pokud je metoda `register` v `cancellation_token` použita pro příjem oznámení o tom, že dojde k zrušení, je objekt `cancellation_token_registration` vrácen jako popisovač zpětného volání, aby volající mohl požadovat konkrétní zpětné volání, které již není provedeno pomocí metody `deregister`.

## <a name="syntax"></a>Syntaxe

```cpp
class cancellation_token_registration;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[cancellation_token_registration](#ctor)||
|[~ cancellation_token_registration destruktor](#dtor)||

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operátor =](#operator_eq)||
|[operator = = – operátor](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`cancellation_token_registration`

## <a name="requirements"></a>Požadavky

**Záhlaví:** pplcancellation_token. h

**Obor názvů:** souběžnost

## <a name="dtor"></a>~ cancellation_token_registration

```cpp
~cancellation_token_registration();
```

## <a name="ctor"></a>cancellation_token_registration

```cpp
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token_registration` ke zkopírování nebo přesunutí.

## <a name="operator_neq"></a>! = – operátor

```cpp
bool operator!= (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`cancellation_token_registration` k porovnání.

### <a name="return-value"></a>Návratová hodnota

## <a name="operator_eq"></a>operátor =

```cpp
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token_registration` k přiřazení.

### <a name="return-value"></a>Návratová hodnota

## <a name="operator_eq_eq"></a>operator = = – operátor

```cpp
bool operator== (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`cancellation_token_registration` k porovnání.

### <a name="return-value"></a>Návratová hodnota

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
