---
title: Platform::Guid – hodnotová třída
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 7c3b89ff238b1cb5ee9fbb71e83d20f571e656a3
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031534"
---
# <a name="platformguid-value-class"></a>Platform::Guid – hodnotová třída

Představuje typ typu [GUID](/windows/win32/api/guiddef/ns-guiddef-guid v systému typu Prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
public value struct Guid
```

### <a name="members"></a>Členové

`Platform::Guid`má `Equals()`, `GetHashCode()`a `ToString()` metody odvozené z [Platform::Object](../cppcx/platform-object-class.md) `GetTypeCode()` Class a metodu odvozenou z [Platform::Type Class](../cppcx/platform-type-class.md). `Platform::Guid`má také následující členy.

|Člen|Popis|
|------------|-----------------|
|[Identifikátor guid](#ctor)|Inicializuje novou instanci `Platform::Guid`.|
|[operátor==](#operator-equality)|Operátor Rovná se.|
|[operátor!=](#operator-inequality)|Není rovná operátor.|
|[Operátor&lt;](#operator-less)|Menší než operátor.|
|[operátor()](#operator-call)|Převede `Platform::Guid` a `GUID`na .|

### <a name="remarks"></a>Poznámky

Chcete-li `Platform::Guid`generovat nový , použijte [Windows::Foundation::GuidHelper::CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid) statickou metodu.

### <a name="requirements"></a>Požadavky

**Minimální podporovaný klient:** Windows 8

**Minimální podporovaný server:** Windows Server 2012

**Obor názvů:** Platforma

**Metadata:** platform.winmd

## <a name="guidguid-constructors"></a><a name="ctor"></a>Guid::Konstruktory guid

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

*A*<br/>
První 4 bajty `GUID`.

*B*<br/>
Další 2 bajty `GUID`.

*C*<br/>
Další 2 bajty `GUID`.

*D*<br/>
Další bajt . `GUID`

*E*<br/>
Další bajt . `GUID`

*F*<br/>
Další bajt . `GUID`

*G*<br/>
Další bajt . `GUID`

*H*<br/>
Další bajt . `GUID`

*I*<br/>
Další bajt . `GUID`

*J*<br/>
Další bajt . `GUID`

*K*<br/>
Další bajt . `GUID`

*M*<br/>
A `GUID` ve formě [struktury GUID](/windows/win32/api/guiddef/ns-guiddef-guid).

*N*<br/>
Zbývajících 8 bajtů `GUID`.

## <a name="guidoperator-operator"></a><a name="operator-equality"></a>Guid::operator== Operátor

Porovná dvě `Platform::Guid` instance rovnosti.

### <a name="syntax"></a>Syntaxe

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*identifikátor GUID1*<br/>
První `Platform::Guid` porovnat.

*guid2*<br/>
Druhý `Platform::Guid` porovnat.

### <a name="return-value"></a>Návratová hodnota

True, pokud `Platform::Guid` jsou dvě instance stejné.

### <a name="remarks"></a>Poznámky

Preferovat `==` použití operátoru namísto [Windows::Foundation::GuidHelper::Rovná se](/uwp/api/windows.foundation.guidhelper.equals) statickou metodu.

## <a name="guidoperator-operator"></a><a name="operator-inequality"></a>Guid::operátor!= Operátor

Porovná dvě `Platform::Guid` instance nerovnosti.

### <a name="syntax"></a>Syntaxe

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*identifikátor GUID1*<br/>
První `Platform::Guid` porovnat.

*guid2*<br/>
Druhý `Platform::Guid` porovnat.

### <a name="return-value"></a>Návratová hodnota

True, pokud `Platform::Guid` dvě instance nejsou stejné.

## <a name="guidoperatorlt-operator"></a><a name="operator-less"></a>Identifikátor Guid::Operátor&lt; operátora

Porovná dvě `Platform::Guid` instance pro řazení.

### <a name="syntax"></a>Syntaxe

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*identifikátor GUID1*<br/>
První `Platform::Guid` porovnat.

*guid2*<br/>
Druhý `Platform::Guid` porovnat.

### <a name="return-value"></a>Návratová hodnota

True, pokud *guid1* je objednáno před *guid2*. Řazení je lexikografické po `Platform::Guid` ošetření každého, jako by se jednalo o pole čtyř 32bitových nepodepsaných hodnot. Toto není řazení používané SQL Server nebo rozhraní .NET Framework, ani není stejné jako lexikografické řazení podle řetězcové reprezentace.

Tento operátor je k `Guid` dispozici tak, aby objekty mohou být snadněji spotřebovány standardní knihovny Jazyka C++.

## <a name="guidoperator-operator"></a><a name="operator-call"></a>Guid::operátor() Operátor

Implicitně převede `Platform::Guid` a na [strukturu GUID](/windows/win32/api/guiddef/ns-guiddef-guid).

### <a name="syntax"></a>Syntaxe

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>Návratová hodnota

[Struktura GUID](/windows/win32/api/guiddef/ns-guiddef-guid).

## <a name="see-also"></a>Viz také

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
