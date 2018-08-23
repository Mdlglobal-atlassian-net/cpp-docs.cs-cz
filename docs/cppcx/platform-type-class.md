---
title: Platform::type – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
dev_langs:
- C++
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4d2931df50c6bfac126bc8e8ab1c70d61bdfe39
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596698"
---
# <a name="platformtype-class"></a>Platform::type – třída
Obsahuje běhových informací o typu – konkrétně řetězec názvu a typecode. Získá voláním [Object::gettype –](../cppcx/platform-object-class.md#gettype) libovolného objektu nebo pomocí [typeid](../windows/typeid-cpp-component-extensions.md) operátor na název třídy nebo struktury.  
  
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
|[Type – operátor ^](../cppcx/operator-type-hat.md)|Umožňuje převod z `Windows::UI::Xaml::Interop::TypeName` k `Platform::Type`.|  
|[operátor Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)|Umožňuje převod z `Platform::Type` k `Windows::UI::Xaml::Interop::TypeName`.|  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serverem:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
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
  
## <a name="see-also"></a>Viz také  
 [Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)