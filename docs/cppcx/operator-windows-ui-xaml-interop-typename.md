---
title: Windows::UI::Xaml::Interop::TypeName – operátor
ms.date: 12/30/2016
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
ms.openlocfilehash: d35056ca1a4e7f06c9f91fe86998a676a12395f2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337002"
---
# <a name="operator-windowsuixamlinteroptypename"></a>Windows::UI::Xaml::Interop::TypeName – operátor

Povolí převod `Platform::Type` z [windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename).

## <a name="syntax"></a>Syntaxe

```cpp
Operator TypeName(Platform::Type^ type);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí [systém Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename) `Platform::Type^`při zadání .

### <a name="remarks"></a>Poznámky

`TypeName`je jazykově neutrální struktura prostředí Windows Runtime pro reprezentaci informací o typu. [Platforma::Typ](../cppcx/platform-type-class.md) je specifický pro C++ a nelze je předat přes binární rozhraní aplikace (ABI). Zde je jedno `TypeName`použití , ve funkci [Navigace:](/uwp/api/windows.ui.xaml.controls.frame.navigate)

```cpp
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `TypeName` `Type`převést mezi a .

```cpp
// Convert from Type to TypeName
Windows::UI::Xaml::Interop::TypeName tn = TypeName(MainPage::typeid);

// Convert back from TypeName to Type
Type^ tx2 = (Type^)(tn);
```

## <a name="net-framework-equivalent"></a>Ekvivalent v rozhraní .NET Framework

Programy rozhraní .NET Framework promítají `TypeName` jako [System.Type](/dotnet/api/system.type).

### <a name="requirements"></a>Požadavky

## <a name="see-also"></a>Viz také

[Windows::UI::Xaml::Interop::TypeName – operátor](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Platform::Type – třída](../cppcx/platform-type-class.md)
