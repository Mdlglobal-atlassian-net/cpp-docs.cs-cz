---
title: Platform::Guid – hodnotová třída
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: bf7d73e1e50bb77a84267f3a5388c07a49c54c79
ms.sourcegitcommit: fbc05d8581913bca6eff664e5ecfcda8e471b8b1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2019
ms.locfileid: "56809695"
---
# <a name="platformguid-value-class"></a>Platform::Guid – hodnotová třída

Představuje [GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931) typu v systému typů modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
public value struct Guid
```

### <a name="members"></a>Členové

`Platform::Guid` má `Equals()`, `GetHashCode()`, a `ToString()` metody odvozený od [Platform::Object – třída](../cppcx/platform-object-class.md)a `GetTypeCode()` metoda odvozený od [Platform::type – třída](../cppcx/platform-type-class.md). `Platform::Guid` také má následující členy.

|Člen|Popis|
|------------|-----------------|
|[identifikátor GUID](#ctor)|Inicializuje novou instanci třídy `Platform::Guid`.|
|[operator==](#operator-equality)|Operátor Equals.|
|[operator!=](#operator-inequality)|Operátor nerovná.|
|[– Operátor&lt;](#operator-less)|Operátor menší než.|
|[operator()](#operator-call)|Převede `Platform::Guid` k `GUID`.|

### <a name="remarks"></a>Poznámky

Generovat nový `Platform::Guid`, použijte [Windows::Foundation::GuidHelper::CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid#Windows_Foundation_GuidHelper_CreateNewGuid) statické metody.

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serveru:** Windows Server 2012

**Namespace:** Platforma

**Metadata:** platform.winmd

## <a name="ctor"></a> GUID::GUID konstruktory

Inicializuje novou instanci třídy `Platform::Guid`.

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
První 4 bajty `GUID`.

*b*<br/>
Další 2 bajty identifikátoru `GUID`.

*c*<br/>
Další 2 bajty identifikátoru `GUID`.

*d*<br/>
Další bajt identifikátoru `GUID`.

*e*<br/>
Další bajt identifikátoru `GUID`.

*f*<br/>
Další bajt identifikátoru `GUID`.

*g*<br/>
Další bajt identifikátoru `GUID`.

*h*<br/>
Další bajt identifikátoru `GUID`.

*i*<br/>
Další bajt identifikátoru `GUID`.

*j*<br/>
Další bajt identifikátoru `GUID`.

*k*<br/>
Další bajt identifikátoru `GUID`.

*m*<br/>
A `GUID` ve formuláři [GUID struktury](https://msdn.microsoft.com/library/windows/desktop/aa373931).

*n*<br/>
Zbývající 8 bajtů `GUID`.

## <a name="operator-equality"></a> GUID::Operator == – operátor

Porovná dva `Platform::Guid` instance pro rovnost.

### <a name="syntax"></a>Syntaxe

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*guid1*<br/>
První `Platform::Guid` k porovnání.

*guid2*<br/>
Druhá `Platform::Guid` k porovnání.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud dva `Platform::Guid` instancí jsou si rovny.

### <a name="remarks"></a>Poznámky

Přednost používání `==` namísto [Windows::Foundation::GuidHelper::Equals](/uwp/api/windows.foundation.guidhelper.equals) statické metody.

## <a name="operator-inequality"></a> GUID::Operator! = – operátor

Porovná dva `Platform::Guid` instance nerovnost.

### <a name="syntax"></a>Syntaxe

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*guid1*<br/>
První `Platform::Guid` k porovnání.

*guid2*<br/>
Druhá `Platform::Guid` k porovnání.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud dva `Platform::Guid` instancí nejsou stejné.

## <a name="operator-less"></a> GUID::Operator&lt; – operátor

Porovná dva `Platform::Guid` instance pro řazení.

### <a name="syntax"></a>Syntaxe

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*guid1*<br/>
První `Platform::Guid` k porovnání.

*guid2*<br/>
Druhá `Platform::Guid` k porovnání.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě *guid1* je řazen před *guid2*. Řazení je po zpracování každého lexikografickým `Platform::Guid` , pokud je pole čtyř hodnot bez znaménka 32-bit. To není řazení systému SQL Server nebo rozhraní .NET Framework, ani je stejný jako lexicographical řazení podle řetězcovou reprezentaci.

Tento operátor se poskytuje tak, aby `Guid` objekty mohou snadněji využívat standardní knihovny C++.

## <a name="operator-call"></a> GUID::Operator() – operátor

Implicitně převede `Platform::Guid` k [GUID struktury](https://msdn.microsoft.com/library/windows/desktop/aa373931).

### <a name="syntax"></a>Syntaxe

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>Návratová hodnota

A [GUID struktury](https://msdn.microsoft.com/library/windows/desktop/aa373931).

## <a name="see-also"></a>Viz také

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
