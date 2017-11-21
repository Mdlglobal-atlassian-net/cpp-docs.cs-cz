---
title: "Delegáti a události | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __event keyword [C++]
- delegate keyword [C++]
- delegates [C++], upgrading from Managed Extensions for C++
- __delegate keyword
- events [C++], upgrading from Managed Extensions for C++
- event keyword [C++]
ms.assetid: 3505c626-7e5f-4492-a947-0e2248f7b84a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 28abb6daf5d778cf2cc7c904440808fd7ca7e48e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="delegates-and-events"></a>Delegáti a události
Způsob deklarace Delegáti a události změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Dvojité podtržítko je již nepotřebujete, jak znázorňuje následující ukázka. Zde je ukázkový kód v spravovaných rozšíření:  
  
```  
__delegate void ClickEventHandler(int, double);  
__delegate void DblClickEventHandler(String*);  
  
__gc class EventSource {  
   __event ClickEventHandler* OnClick;    
   __event DblClickEventHandler* OnDblClick;    
};  
```  
  
 Stejný kód v nové syntaxe vypadá takto:  
  
```  
delegate void ClickEventHandler( int, double );  
delegate void DblClickEventHandler( String^ );  
  
ref class EventSource {  
   event ClickEventHandler^ OnClick;   
   event DblClickEventHandler^ OnDblClick;   
};  
```  
  
 Události (a delegáti) jsou odkazové typy, což je zrušte v nové syntaxe z důvodu použití hat (`^`).  Události podporují syntaxi explicitní deklarace i triviální formu uvedenou v předchozí kód. Ve formuláři explicitní uživatel zadá `add`, `raise`, a `remove` metody přidružený k události. (Jenom `add` a `remove` metody jsou požadovány; `raise` metoda je volitelný.)  
  
 V části spravovaných rozšíření Pokud zadáte tyto metody, také nezadáte explicitní deklaraci události, ale musíte se rozhodnout na název pro událost, která není k dispozici. Každá metoda je zadána ve formátu `add_EventName`, `raise_EventName`, a `remove_EventName`, jako v následujícím příkladu převzat ze spravovaných rozšíření specifikace:  
  
```  
// explicit implementations of add, remove, raise  
public __delegate void f(int);  
public __gc struct E {  
   f* _E;  
public:  
   E() { _E = 0; }  
  
   __event void add_E1(f* d) { _E += d; }  
  
   static void Go() {  
      E* pE = new E;  
      pE->E1 += new f(pE, &E::handler);  
      pE->E1(17);   
      pE->E1 -= new f(pE, &E::handler);  
      pE->E1(17);   
   }  
  
private:  
   __event void raise_E1(int i) {  
      if (_E)  
         _E(i);  
   }  
  
protected:  
   __event void remove_E1(f* d) {  
      _E -= d;  
   }  
};  
```  
  
 Nové syntaxe zjednodušuje deklaraci, jak ukazuje následující překlad. Událost určuje dva nebo tři metody uzavřené v páru složené závorky a umístit ihned po deklaraci události a související delegáta typu, jak je vidět tady:  
  
```  
public delegate void f( int );  
public ref struct E {  
private:  
   f^ _E; // delegates are also reference types  
  
public:  
   E() {  // note the replacement of 0 with nullptr!  
      _E = nullptr;   
   }  
  
   // the new aggregate syntax of an explicit event declaration  
   event f^ E1 {  
   public:  
      void add( f^ d ) {  
         _E += d;  
      }  
  
   protected:  
      void remove( f^ d ) {  
         _E -= d;  
      }  
  
   private:  
      void raise( int i ) {  
         if ( _E )  
            _E( i );  
      }  
   }  
  
   static void Go() {  
      E^ pE = gcnew E;  
      pE->E1 += gcnew f( pE, &E::handler );  
      pE->E1( 17 );   
      pE->E1 -= gcnew f( pE, &E::handler );  
      pE->E1( 17 );   
   }  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Deklarace členů v rámci třídy nebo rozhraní (C + +/ CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [Delegát (rozšíření komponent C++)](../windows/delegate-cpp-component-extensions.md)   
 [události](../windows/event-cpp-component-extensions.md)