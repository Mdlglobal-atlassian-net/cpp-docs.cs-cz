---
title: "Soukromé virtuální funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- virtual functions, private
- derived classes, virtual functions
- access modifiers [C++], for class members
- member access [C++], virtual members
ms.assetid: 04448086-bf72-44be-9c1f-dfda1744949e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9b407bc469a345706f99cf5bad578f678e652a4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="private-virtual-functions"></a>Soukromé virtuální funkce
Způsob, jakým soukromé virtuální funkce jsou zpracovány v odvozených třídách změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Ve spravovaných rozšíření úroveň přístupu virtuální funkce neuvádělo její možnosti k přepsání v odvozené třídě. V nové syntaxe virtuální funkci nelze přepsat virtuální funkce základní třídy, která nemůže získat přístup. Příklad:  
  
```  
__gc class MyBaseClass {  
   // inaccessible to a derived class   
   virtual void g();  
};  
  
__gc class MyDerivedClass : public MyBaseClass {  
public:  
   // okay in Managed Extensions; g() overrides MyBaseClass::g()  
   // error in new syntax; cannot override: MyBaseClass::g() is inaccessible  
   void g();  
};  
```  
  
 Neexistuje žádné skutečné mapování tohoto druhu návrhu na nové syntaxe. Uživatel jednoduše musí zpřístupnit členy základní třídy – to znamená, ne privátní. Zděděné metody nemusíte stejný přístup. V tomto příkladu je nejméně invazivní změnit nastavte člena MyBaseClass `protected`. Tímto způsobem obecné program přístup k metodě prostřednictvím MyBaseClass stále zakázán.  
  
```  
ref class MyBaseClass {  
protected:  
   virtual void g();  
};  
  
ref class MyDerivedClass : MyBaseClass {  
public:  
   virtual void g() override;  
};  
```  
  
 Všimněte si, že neexistence explicitního `virtual` – klíčové slovo v základní třídě podle nové syntaxe, vygeneruje upozornění.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace členů v rámci třídy nebo rozhraní (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 