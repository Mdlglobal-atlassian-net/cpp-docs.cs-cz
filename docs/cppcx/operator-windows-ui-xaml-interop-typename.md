---
title: operátor Windows::UI::Xaml::Interop::TypeName | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 714d39a70b19998a5daddceadc2c91df65312122
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34256312"
---
# <a name="operator-windowsuixamlinteroptypename"></a>Windows::UI::Xaml::Interop::TypeName – operátor
Umožňuje převod `Platform::Type` k [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Operator TypeName(Platform::Type^ type)  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) při zadané `Platform::Type^`.  
  
### <a name="remarks"></a>Poznámky  
 `TypeName` je struktura prostředí Windows Runtime jazykově neutrální pro představující informace o typu. [Platform::type](../cppcx/platform-type-class.md) je specifický pro C++ a nemůže být předán přes rozhraní binární aplikace (ABI). Tady je jedno použití `TypeName`v [přejděte](http://msdn.microsoft.com/library/windows/apps/hh702394.aspx) funkce:  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
### <a name="example"></a>Příklad  
 Další příklad ukazuje, jak převést mezi `TypeName` a `Type`.  
  
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
 [operátor Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)   
 [Platform::Type – třída](../cppcx/platform-type-class.md)