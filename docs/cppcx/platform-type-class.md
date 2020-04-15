---
title: Platform::Type – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
ms.openlocfilehash: 7463a2518e6ec5cc84f59db05cfaf60e43eb9fde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322097"
---
# <a name="platformtype-class"></a>Platform::Type – třída

Obsahuje informace o typu za běhu – konkrétně název řetězce a kód typu. Získané voláním [Object::GetType](../cppcx/platform-object-class.md#gettype) na libovolný objekt nebo pomocí operátoru [typeid](../extensions/typeid-cpp-component-extensions.md) na název třídy nebo struktury.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>Poznámky

Třída `Type` je užitečná v aplikacích, `if` které `switch` musí přímé zpracování pomocí nebo příkaz, který větve založené na typu run-time objektu. Kód typu, který popisuje kategorii typu, je načten pomocí členské funkce [Type::GetTypeCode.](#gettypecode)

## <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|[Typ::Metoda GetTypeCode](#gettypecode)|Vrátí [hodnotu výčtu platformy::TypeCode pro](../cppcx/platform-typecode-enumeration.md) objekt.|
|[Typ::Metoda ToString](#tostring)|Vrátí název typu, jak je zadánv jeho metadata.|

## <a name="public-properties"></a>Veřejné nemovitosti

|||
|-|-|
|[Text::FullName](#fullname)|Vrátí [platformu::String Class](../cppcx/platform-string-class.md)^ , která představuje plně kvalifikovaný název typu a používá . (tečka) jako oddělovač, ne :: (dvojitá `MyNamespace.MyClass`dvojtečka)—například .|

## <a name="conversion-operators"></a>Operátory převodu

|||
|-|-|
|[typ operátora^](../cppcx/operator-type-hat.md)|Umožňuje převod `Windows::UI::Xaml::Interop::TypeName` `Platform::Type`z na .|
|[Windows::UI::Xaml::Interop::TypeName – operátor](../cppcx/operator-windows-ui-xaml-interop-typename.md)|Umožňuje převod `Platform::Type` `Windows::UI::Xaml::Interop::TypeName`z na .|

### <a name="requirements"></a>Požadavky

**Minimální podporovaný klient:** Windows 8

**Minimální podporovaný server:** Windows Server 2012

**Obor názvů:** Platforma

**Metadata:** platform.winmd

## <a name="typefullname-property"></a><a name="fullname"></a>Text::Vlastnost FullName

Načte plně kvalifikovaný název aktuálního typu `Namespace.Type`ve formuláři .

### <a name="syntax"></a>Syntaxe

```cpp
String^ FullName();
```

### <a name="return-value"></a>Návratová hodnota

Název typu

### <a name="example"></a>Příklad

```cpp
//  namespace is TestApp
MainPage::MainPage()
{
    InitializeComponent();
    Type^ t = this->GetType();
    auto s = t->FullName; // returns "TestApp.MainPage"
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"
}
```

## <a name="typegettypecode-method"></a><a name="gettypecode"></a>Typ::Metoda GetTypeCode

Načte předdefinovanou kategorii číselného typu.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>Návratová hodnota

Jedna z platformy::TypeCode výčtové hodnoty.

### <a name="remarks"></a>Poznámky

Ekvivalent GetTypeCode() členské metody je `typeid` vlastnost.

## <a name="typetostring-method"></a><a name="tostring"></a>Typ::Metoda ToString

Načte název typu.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>Návratová hodnota

Název typu, jak je zadán v jeho metadata.

## <a name="see-also"></a>Viz také

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
