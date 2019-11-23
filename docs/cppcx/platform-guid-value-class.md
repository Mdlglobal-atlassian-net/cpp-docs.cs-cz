---
title: Platform::Guid – hodnotová třída
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: f63b2bb4fd5f809861622a4f6b255ee3725564b6
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816583"
---
# <a name="platformguid-value-class"></a>Platform::Guid – hodnotová třída

Představuje typ [GUID](/previous-versions/cc317743(v%3dmsdn.10)) v systému prostředí Windows Runtimeho typu.

## <a name="syntax"></a>Syntaxe

```cpp
public value struct Guid
```

### <a name="members"></a>Members

`Platform::Guid` má metody `Equals()`, `GetHashCode()`a `ToString()` odvozené z [třídy Platform:: Object](../cppcx/platform-object-class.md)a `GetTypeCode()` metody odvozené z [třídy Platform:: Type](../cppcx/platform-type-class.md). `Platform::Guid` mají také následující členy.

|Člen|Popis|
|------------|-----------------|
|[Hlavních](#ctor)|Inicializuje novou instanci `Platform::Guid`.|
|[operator==](#operator-equality)|Operátor Equals|
|[operator!=](#operator-inequality)|Operátor nerovnosti|
|[operátor&lt;](#operator-less)|Operátor menší než|
|[operator()](#operator-call)|Převede `Platform::Guid` na `GUID`.|

### <a name="remarks"></a>Poznámky

Chcete-li vygenerovat nový `Platform::Guid`, použijte statickou metodu [Windows:: Foundation:: GuidHelper:: CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid#Windows_Foundation_GuidHelper_CreateNewGuid) .

### <a name="requirements"></a>Požadavky

**Minimální podporovaný klient:** Systém Windows 8

**Minimální podporovaný Server:** Windows Server 2012

**Obor názvů:** Platformy

**Metadata:** Platform. winmd

## <a name="ctor"></a>GUID:: GUID – konstruktory

Inicializuje novou instanci `Platform::Guid`.

### <a name="syntax"></a>Syntaxe

```cpp
Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    unsigned char d,
    unsigned char e,
    unsigned char f,
    unsigned char g,
    unsigned char h,
    unsigned char i,
    unsigned char j,
    unsigned char k );

Guid(GUID m);

Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    Array<unsigned char>^ n );
```

### <a name="parameters"></a>Parametry

*a*<br/>
Prvních 4 bajtů `GUID`.

*b*<br/>
Dalších 2 bajtů `GUID`.

*c*<br/>
Dalších 2 bajtů `GUID`.

*d*<br/>
Další bajt `GUID`.

*e*<br/>
Další bajt `GUID`.

*f*<br/>
Další bajt `GUID`.

*g*<br/>
Další bajt `GUID`.

*h*<br/>
Další bajt `GUID`.

*i*<br/>
Další bajt `GUID`.

*j*<br/>
Další bajt `GUID`.

*k*<br/>
Další bajt `GUID`.

*m*<br/>
`GUID` ve formě [struktury GUID](/previous-versions/cc317743(v%3dmsdn.10)).

*n*<br/>
Zbývajících 8 bajtů `GUID`.

## <a name="operator-equality"></a>GUID:: operator = = – operátor

Porovná dvě instance `Platform::Guid` pro rovnost.

### <a name="syntax"></a>Syntaxe

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*guid1*<br/>
První `Platform::Guid` k porovnání

*guid2*<br/>
Druhý `Platform::Guid` k porovnání.

### <a name="return-value"></a>Návratová hodnota

True, pokud jsou tyto dvě instance `Platform::Guid` stejné.

### <a name="remarks"></a>Poznámky

Raději použijte operátor `==` namísto statické metody [Windows:: Foundation:: GuidHelper:: Equals](/uwp/api/windows.foundation.guidhelper.equals) .

## <a name="operator-inequality"></a>GUID:: operator! = – operátor

Porovná dvě instance `Platform::Guid` pro nerovnost.

### <a name="syntax"></a>Syntaxe

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*guid1*<br/>
První `Platform::Guid` k porovnání

*guid2*<br/>
Druhý `Platform::Guid` k porovnání.

### <a name="return-value"></a>Návratová hodnota

True, pokud se tyto dvě instance `Platform::Guid` neshodují.

## <a name="operator-less"></a>GUID:: operator&lt; – operátor

Porovná dvě instance `Platform::Guid` pro řazení.

### <a name="syntax"></a>Syntaxe

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*guid1*<br/>
První `Platform::Guid` k porovnání

*guid2*<br/>
Druhý `Platform::Guid` k porovnání.

### <a name="return-value"></a>Návratová hodnota

True, pokud je *guid1* seřazen před *guid2*. Řazení je lexikografickým pořadím, když se každý `Platform::Guid` zpracuje, jako by to bylo pole 4 32 nepodepsaných hodnot. Toto není řazení, které používá SQL Server nebo .NET Framework, ani to stejné jako řazení lexicographical podle řetězcové reprezentace.

Tento operátor je k dispozici, aby bylo možné `Guid` objekty snadněji využívané C++ standardní knihovnou.

## <a name="operator-call"></a>GUID:: operator () – operátor

Implicitně převede `Platform::Guid` na [strukturu identifikátoru GUID](/previous-versions/cc317743(v%3dmsdn.10)).

### <a name="syntax"></a>Syntaxe

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>Návratová hodnota

[Struktura identifikátoru GUID](/previous-versions/cc317743(v%3dmsdn.10)).

## <a name="see-also"></a>Viz také:

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
