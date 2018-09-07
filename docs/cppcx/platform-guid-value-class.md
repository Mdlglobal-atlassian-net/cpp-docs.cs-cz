---
title: Platform::GUID – hodnotová třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
dev_langs:
- C++
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e115cf74eaac194c9e5b7154898cc23e10b220eb
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100428"
---
# <a name="platformguid-value-class"></a>Platform::Guid – hodnotová třída

Představuje [GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx) typu v systému typů modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
public value struct Guid
```

### <a name="members"></a>Členové

Identifikátor GUID má metody Equals() GetHashCode(), a metody ToString() odvozený od [Platform::Object – třída](../cppcx/platform-object-class.md), a metodu GetTypeCode() odvozený od [Platform::type – třída](../cppcx/platform-type-class.md). Identifikátor GUID má také následující členy.

|Člen|Popis|
|------------|-----------------|
|[identifikátor GUID](#ctor)|Inicializuje novou instanci struktury identifikátor Guid.|
|[operator==](#operator-equality)|Operátor Equals.|
|[operator!=](#operator-not-equal)|Operátor nerovná.|
|[Operator()](#operator-call)|Identifikátor Guid se převede na identifikátor GUID.|

### <a name="remarks"></a>Poznámky

Příklad toho, jak generovat nové Platform::GUID – použití funkce Windows [CoCreateGuid](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateguid), naleznete v tématu [komponenty WinRT: jak vygenerovat identifikátor GUID?](http://blogs.msdn.com/b/eternalcoding/archive/2013/03/25/winrt-component-how-to-generate-a-guid.aspx)

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serverem:** systému Windows Server 2012

**Namespace:** platformy

**Metadata:** platform.winmd

## <a name="ctor"></a> GUID::GUID konstruktory

Inicializuje novou instanci struktury identifikátor Guid.

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
První 4 bajty identifikátoru GUID.

*b*<br/>
Další 2 bajty identifikátoru GUID.

*c*<br/>
Další 2 bajty identifikátoru GUID.

*d*<br/>
Další bajt identifikátoru GUID.

*e*<br/>
Další bajt identifikátoru GUID.

*f*<br/>
Další bajt identifikátoru GUID.

*g*<br/>
Další bajt identifikátoru GUID.

*h*<br/>
Další bajt identifikátoru GUID.

*i*<br/>
Další bajt identifikátoru GUID.

*j*<br/>
Další bajt identifikátoru GUID.

*k*<br/>
Další bajt identifikátoru GUID.

*m*<br/>
Identifikátor GUID, jak jsou definovány.

*n*<br/>
8 zbývající bajty identifikátoru GUID.

## <a name="operator-equality"></a> GUID::Operator == – operátor

Porovná dva identifikátory GUID.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::Guid::operator==
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud jsou si rovny dva identifikátory GUID.

## <a name="operator-inequality"></a> GUID::Operator! = – operátor

Porovná dva identifikátory GUID.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::Guid::operator!=
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud dva identifikátory GUID nejsou stejné.

## <a name="operator-call"></a> GUID::Operator() – operátor

Implicitně převede [GUID struktury](https://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx)Platform::GUID – identifikátor GUID.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::Guid operator();
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor Guid struktury.

## <a name="see-also"></a>Viz také

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)