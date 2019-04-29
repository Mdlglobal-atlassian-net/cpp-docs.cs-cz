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
ms.openlocfilehash: c6ca8061181ec057110282fa297666235e898ff6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62414188"
---
# <a name="cancellationtokenregistration-class"></a>cancellation_token_registration – třída

`cancellation_token_registration` Třída představuje zpětné volání upozornění z `cancellation_token`. Když `register` metodu na `cancellation_token` slouží k přijímání oznámení tom, kdy kde zrušení dojde, `cancellation_token_registration` objekt je vrácen jako popisovač pro zpětné volání tak, aby volající mohl požadovat konkrétní zpětné volání již nebude provedeno pomocí `deregister` metody.

## <a name="syntax"></a>Syntaxe

```
class cancellation_token_registration;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[cancellation_token_registration](#ctor)||
|[~ cancellation_token_registration – destruktor](#dtor)||

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operátor =](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`cancellation_token_registration`

## <a name="requirements"></a>Požadavky

**Záhlaví:** pplcancellation_token.h

**Namespace:** souběžnosti

##  <a name="dtor"></a> ~cancellation_token_registration

```
~cancellation_token_registration();
```

##  <a name="ctor"></a> cancellation_token_registration –

```
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token_registration` Má zkopírovat nebo přesunout.

##  <a name="operator_neq"></a> Operator! =

```
bool operator!= (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`cancellation_token_registration` k porovnání.

### <a name="return-value"></a>Návratová hodnota

##  <a name="operator_eq"></a> operátor =

```
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token_registration` Přiřadit.

### <a name="return-value"></a>Návratová hodnota

##  <a name="operator_eq_eq"></a> Operator ==

```
bool operator== (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`cancellation_token_registration` k porovnání.

### <a name="return-value"></a>Návratová hodnota

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)
