---
title: Type^ – operátor
ms.date: 12/30/2016
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
ms.openlocfilehash: fca53abb9dc17588695591d496b7db2a76e319f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553657"
---
# <a name="operator-type"></a>Type^ – operátor

Umožňuje převod z [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) k `Platform::Type`.

## <a name="syntax"></a>Syntaxe

```cpp
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `Platform::Type` když [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx).

### <a name="remarks"></a>Poznámky

`TypeName` je struktura prostředí Windows Runtime jazykově neutrální představující informace o typu. [Platform::type –](../cppcx/platform-type-class.md) je specifická pro C++ a nelze předat jako napříč binárním rozhraním aplikace (ABI). Tady je jedno použití `TypeName`v [Navigovat](https://msdn.microsoft.com/library/windows/apps/hh702394.aspx) funkce:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak převést mezi `TypeName` a `Type`.

```

// Convert from Type to TypeName
TypeName tn = TypeName(MainPage::typeid);

// Convert back from TypeName to Type
Type^ tx2 = (Type^)(tn);
```

## <a name="net-framework-equivalent"></a>Ekvivalent v rozhraní .NET Framework

Rozhraní .NET framework projektu programy `TypeName` jako <xref:System.Type>

### <a name="requirements"></a>Požadavky

## <a name="see-also"></a>Viz také

[operátor Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Platform::Type – třída](../cppcx/platform-type-class.md)