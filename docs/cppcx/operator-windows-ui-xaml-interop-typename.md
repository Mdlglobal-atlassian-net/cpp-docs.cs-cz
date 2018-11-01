---
title: Windows::UI::Xaml::Interop::TypeName – operátor
ms.date: 12/30/2016
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
ms.openlocfilehash: c77655ed7692c4cdccc311bc27c492126d62e54e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659210"
---
# <a name="operator-windowsuixamlinteroptypename"></a>Windows::UI::Xaml::Interop::TypeName – operátor

Umožňuje převod z `Platform::Type` k [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx).

## <a name="syntax"></a>Syntaxe

```cpp
Operator TypeName(Platform::Type^ type);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) když `Platform::Type^`.

### <a name="remarks"></a>Poznámky

`TypeName` je struktura prostředí Windows Runtime jazykově neutrální představující informace o typu. [Platform::type –](../cppcx/platform-type-class.md) je specifická pro C++ a nelze předat jako napříč binárním rozhraním aplikace (ABI). Tady je jedno použití `TypeName`v [Navigovat](https://msdn.microsoft.com/library/windows/apps/hh702394.aspx) funkce:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak převést mezi `TypeName` a `Type`.

```

// Convert from Type to TypeName
Windows::UI::Xaml::Interop::TypeName tn = TypeName(MainPage::typeid);

// Convert back from TypeName to Type
Type^ tx2 = (Type^)(tn);
```

## <a name="net-framework-equivalent"></a>Ekvivalent v rozhraní .NET Framework

Rozhraní .NET framework projektu programy `TypeName` jako [System.Type](assetId:///System.Type?qualifyHint=False&autoUpgrade=True).

### <a name="requirements"></a>Požadavky

## <a name="see-also"></a>Viz také

[operátor Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Platform::Type – třída](../cppcx/platform-type-class.md)