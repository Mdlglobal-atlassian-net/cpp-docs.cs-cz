---
title: "Explicitní přepsání člena rozhraní | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- virtual functions, explicit overrides
- overriding functions
- interface members, explicit overrides
- functions [C++], overriding
- explicit override of virtual function
ms.assetid: 46f1f536-bf43-4311-9a17-ff2282e528a9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 85681b2e2aeeb6dbeb6ffdf511827fb1fc1cb029
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="explicit-override-of-an-interface-member"></a>Explicitní přepsání člena rozhraní
Syntaxe deklarace explicitní přepsání člena rozhraní v rámci třídy změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Často byste chtěli poskytnout dvě instance člena rozhraní v rámci třídy, která implementuje rozhraní – jeden, který se používá při manipulaci s objekty tříd prostřednictvím popisovače rozhraní a ten, který se používá při třída objekty se používají prostřednictvím rozhraní třídy. Příklad:  
  
```  
public __gc class R : public ICloneable {  
   // to be used through ICloneable  
   Object* ICloneable::Clone();  
  
   // to be used through an R  
   R* Clone();  
};  
```  
  
 Ve spravovaných rozšíření jsme to provést tím, že poskytuje explicitní deklaraci metodu rozhraní s názvem metody kvalifikovaný pomocí názvu rozhraní. Instance konkrétní třídy neúplné. Tím se eliminuje potřeba přetypování dolů návratová hodnota `Clone`, v tomto příkladu při explicitní volání prostřednictvím instance `R`.  
  
 V nové syntaxe obecný mechanismus přepsání je zavedený který nahrazuje spravovaných rozšíření syntaxe. Našem příkladu by byl přepsán takto:  
  
```  
public ref class R : public ICloneable {  
public:  
   // to be used through ICloneable  
   virtual Object^ InterfaceClone() = ICloneable::Clone;  
  
   // to be used through an R  
   virtual R^ Clone();  
};  
```  
  
 Tato revize vyžaduje, aby explicitně přepsání člena rozhraní zadat jedinečný název v rámci třídy. Zde jsme zadali nevhodný název pro `InterfaceClone`. Chování je dál stejná – vyvolání prostřednictvím `ICloneable` rozhraní vyvolá přejmenované `InterfaceClone`, zatímco volání prostřednictvím objektu typu `R` vyvolá druhý `Clone` instance.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace členů v rámci třídy nebo rozhraní (C + +/ CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [Explicitní přepsání](../windows/explicit-overrides-cpp-component-extensions.md)