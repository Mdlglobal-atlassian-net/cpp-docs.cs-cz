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
ms.openlocfilehash: 6685edbe2e6e4805cadb38ada55624eaec2a7ce8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Deklarace členů v rámci třídy nebo rozhraní (C + +/ CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 