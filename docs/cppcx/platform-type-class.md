---
title: "Třída Platform::type | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
dev_langs: C++
helpviewer_keywords: Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 260a7f5a8d5a100edd6995c381a79b5552c0744b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="platformtype-class"></a>Platform::type – třída
Obsahuje informace o běhu o typu – konkrétně řetězec název a typ objektu typecode. Získá voláním [Object::gettype –](../cppcx/platform-object-class.md#gettype) libovolného objektu nebo nebo pomocí [typeid](../windows/typeid-cpp-component-extensions.md) operátor na třídě nebo struktuře název.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class Platform::Type :      
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable  
```  
  
### <a name="remarks"></a>Poznámky  
 `Type` Třída je užitečná v aplikacích, které musí směrovat zpracování pomocí `if` nebo `switch` příkaz, který větví na základě spuštění typu objektu. Zadejte kód, který popisuje kategorie typu je načíst s použitím [Type::GetTypeCode](#gettypecode) – členská funkce.  
  
## <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|[Type::GetTypeCode – metoda](#gettypecode)|Vrátí [Platform::TypeCode výčtu](../cppcx/platform-typecode-enumeration.md) hodnotu objektu.| 
|[Type::ToString – metoda](#tostring)|Vrátí název typu uvedeného ve svých metadatech.| 

 
## <a name="public-properties"></a>Veřejné vlastnosti  
  
|||  
|-|-|  
|[Type::fullname](#fullname)|Vrátí [Platform::String třída](../cppcx/platform-string-class.md)^, představuje plně kvalifikovaný název typu a používá. (tečka) jako oddělovač, není:: (dvě dvojtečky) – například `MyNamespace.MyClass`.|  
  
## <a name="conversion-operators"></a>Operátory převodu  
  
|||  
|-|-|  
|[Type – operátor ^](../cppcx/operator-subtracttype-hat.md)|Umožňuje převod `Windows::UI::Xaml::Interop::TypeName` k `Platform::Type`.|  
|[operátor Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-subtractwindows-ui-xaml-interop-typename.md)|Umožňuje převod `Platform::Type` k `Windows::UI::Xaml::Interop::TypeName`.|  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd  

 
## <a name="fullname"></a>Vlastnost Type::fullname
Načte plně kvalifikovaný název aktuální typ ve tvaru `Namespace.Type`.  
  
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
  


## <a name="gettypecode"></a>Type::GetTypeCode – metoda
Načte kategorie vestavěné typy číselného typu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Platform::TypeCode GetTypeCode();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden z Platform::TypeCode uvedené hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Je ekvivalentem metodou member GetTypeCode() `typeid` vlastnost.

## <a name="tostring"></a>Type::ToString – metoda
Načte název typu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Platform::String^ ToString();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název typu uvedeného ve svých metadatech.    
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)