---
title: Platform::type – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
ms.openlocfilehash: 456dbff652c8f1b800308ff757930b425616a83f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781741"
---
# <a name="platformtype-class"></a>Platform::type – třída

Obsahuje běhových informací o typu – konkrétně řetězec názvu a typecode. Získá voláním [Object::gettype –](../cppcx/platform-object-class.md#gettype) libovolného objektu nebo pomocí [typeid](../extensions/typeid-cpp-component-extensions.md) operátor na název třídy nebo struktury.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>Poznámky

`Type` Třída je užitečná v aplikacích, které musí směrovat zpracování s použitím `if` nebo `switch` příkaz, který větví na základě run-time typu objektu. Zadejte kód, který popisuje kategorie typu je načíst s použitím [Type::GetTypeCode](#gettypecode) členskou funkci.

## <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|[Type::GetTypeCode – metoda](#gettypecode)|Vrátí [Platform::TypeCode – výčet](../cppcx/platform-typecode-enumeration.md) hodnotu objektu.|
|[Type::ToString – metoda](#tostring)|Vrátí název typu, jak je uvedeno ve svých metadatech.|

## <a name="public-properties"></a>Veřejné vlastnosti

|||
|-|-|
|[Type::FullName](#fullname)|Vrátí [Platform::String – třída](../cppcx/platform-string-class.md)^, který představuje plně kvalifikovaný název typu a používá. (tečka) jako oddělovač, nikoli:: (dvojtečka) – například `MyNamespace.MyClass`.|

## <a name="conversion-operators"></a>operátory převodu

|||
|-|-|
|[operator Type^](../cppcx/operator-type-hat.md)|Umožňuje převod z `Windows::UI::Xaml::Interop::TypeName` k `Platform::Type`.|
|[operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)|Umožňuje převod z `Platform::Type` k `Windows::UI::Xaml::Interop::TypeName`.|

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serveru:** Windows Server 2012

**Namespace:** Platforma

**Metadata:** platform.winmd

## <a name="fullname"></a> Vlastnost Type::fullname

Načte plně kvalifikovaný název typu aktuální ve formě `Namespace.Type`.

### <a name="syntax"></a>Syntaxe

```cpp
String^ FullName();
```

### <a name="return-value"></a>Návratová hodnota

Název typu.
### <a name="example"></a>Příklad

```

//  namespace is TestApp
MainPage::MainPage()
{
    InitializeComponent();
    Type^ t = this->GetType();
    auto s = t->FullName; // returns "TestApp.MainPage"
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"
}
```

## <a name="gettypecode"></a> Type::GetTypeCode – metoda

Načte kategorie číselného typu předdefinovaných typů.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>Návratová hodnota

Jeden Platform::TypeCode – hodnot výčtu.

### <a name="remarks"></a>Poznámky

Je ekvivalentem metodu member GetTypeCode() `typeid` vlastnost.

## <a name="tostring"></a> Type::ToString – metoda

Načte název typu.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>Návratová hodnota

Název typu, jak je uvedeno ve svých metadatech.

## <a name="see-also"></a>Viz také:

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
