---
title: operátor Windows::UI::Xaml::Interop::TypeName | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0cf5041e6e3faa8c495d52c31d86ff25c903a174
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600717"
---
# <a name="operator-windowsuixamlinteroptypename"></a>Windows::UI::Xaml::Interop::TypeName – operátor
Umožňuje převod z `Platform::Type` k [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Operator TypeName(Platform::Type^ type)  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) když `Platform::Type^`.  
  
### <a name="remarks"></a>Poznámky  
 `TypeName` je struktura prostředí Windows Runtime jazykově neutrální představující informace o typu. [Platform::type –](../cppcx/platform-type-class.md) je specifická pro C++ a nelze předat jako napříč binárním rozhraním aplikace (ABI). Tady je jedno použití `TypeName`v [Navigovat](http://msdn.microsoft.com/library/windows/apps/hh702394.aspx) funkce:  
  
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
 [operátor Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)   
 [Platform::Type – třída](../cppcx/platform-type-class.md)