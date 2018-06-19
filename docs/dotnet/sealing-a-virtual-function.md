---
title: Zapečetění virtuální funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
- derived classes, virtual functions
- virtual functions, sealing
- __sealed keyword
ms.assetid: 0e9fae03-6425-4512-9a24-8ccb6dc8a0d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c85f4775025d3661fdfbf8967b310fb733f452b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164593"
---
# <a name="sealing-a-virtual-function"></a>Zapečetění virtuální funkce
Syntaxe pro zapečetění virtuální funkce změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 `__sealed` – Klíčové slovo v spravovaných rozšíření slouží k úpravě buď odkaz na typ, zakazuje následné odvození z něj (najdete v části [deklaraci typu třídy spravované](../dotnet/declaration-of-a-managed-class-type.md)), nebo upravit virtuální funkce zakazuje následné přepsání metody v odvozené třídě. Příklad:  
  
```  
__gc class base { public: virtual void f(); };  
__gc class derived : public base {  
public:  
   __sealed void f();  
};  
```  
  
 V tomto příkladu `derived::f()` přepsání `base::f()` instance založené na přesné shody prototypu funkce. `__sealed` – Klíčové slovo označuje, že následná třída zděděná z odvozené třídy nemůže poskytnout přepsání `derived::f()`.  
  
 V nové syntaxe `sealed` je umístěno za podpisu a ne kdekoli před funkce skutečného prototyp, jak tomu bylo dříve. Kromě toho používání `sealed` vyžaduje explicitní použití `virtual` také – klíčové slovo. To znamená, správný překlad `derived`výše, vypadá takto:  
  
```  
ref class derived: public base {  
public:  
   virtual void f() override sealed;  
};  
```  
  
 Neexistence `virtual` – klíčové slovo v této instanci výsledkem chyba. V nové syntaxe kontextové klíčové slovo `abstract` lze místě `=0` udávajících čistou virtuální funkci. Tato možnost není podporována v rámci spravovaných rozšíření. Příklad:  
  
```  
__gc class base { public: virtual void f()=0; };  
```  
  
 může být přepsán jako  
  
```  
ref class base { public: virtual void f() abstract; };  
```  
  
## <a name="see-also"></a>Viz také  
 [Deklarace členů v rámci třídy nebo rozhraní (C + +/ CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [sealed](../windows/sealed-cpp-component-extensions.md)