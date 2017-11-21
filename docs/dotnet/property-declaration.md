---
title: Deklarace vlastnosti | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __property keyword
- declaring properties, C++
- property keyword [C++]
ms.assetid: de169378-a8b8-49f4-a586-76bffc9b5c9f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c695bfded782ca4db60618ee556af2b4d2dd69be
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="property-declaration"></a>Deklarace vlastnosti
Způsob, jak můžete deklarovat vlastnost v třídě spravované změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Ve spravovaných rozšíření návrh, každý `set` nebo `get` přistupujícího objektu vlastnosti je zadán jako metodu nezávislé. Deklarace každé metody je s předponou `__property` – klíčové slovo. Název metody začíná buď `set_` nebo `get_` a skutečný název vlastnosti (jako viditelné pro uživatele). Proto `Vector` poskytuje `x` koordinaci `get` , vlastnost `get_x` a uživatel by měl vyvolat jej jako `x`. Tuto zásady vytváření názvů a samostatná specifikace metod představuje ve skutečnosti základní implementaci runtime vlastnosti. Zde je ukázka, naše `Vector` sadu souřadnice vlastností:  
  
```  
public __gc __sealed class Vector {  
public:  
   __property double get_x(){ return _x; }  
   __property double get_y(){ return _y; }  
   __property double get_z(){ return _z; }  
  
   __property void set_x( double newx ){ _x = newx; }  
   __property void set_y( double newy ){ _y = newy; }  
   __property void set_z( double newz ){ _z = newz; }  
};  
```  
  
 To rozkládá funkci přidružené vlastnosti a vyžaduje, aby uživatel k lexikálně sjednocení přidružené nastaví a získá. Kromě toho je verbose. V nové syntaxe, což je více než u jazyka C#, `property` – klíčové slovo je následovaný typem vlastnosti a jeho prostým názvem. `set` a `get` metody přístupu jsou umístěny v rámci bloku následující název vlastnosti. Všimněte si, že na rozdíl od C#, podpis metoda přístupu není zadán. Tady je příklad výše uvedeném příkladu kódu přeložit na nové syntaxe.  
  
```  
public ref class Vector sealed {   
public:  
   property double x {  
      double get() {  
         return _x;  
      }  
  
      void set( double newx ) {  
         _x = newx;  
      }  
   } // Note: no semi-colon  
};  
```  
  
 Pokud metody přístupu k vlastnosti reflektuje odlišně úrovně přístupu – například `public get` a `private` nebo `protected set`, můžete zadat explicitní přístup popisku. Ve výchozím nastavení odráží úroveň přístupu vlastnosti u nadřazených úroveň přístupu. Například ve výše uvedené definice `Vector`, i `get` a `set` metody jsou `public`. Chcete-li `set` metoda `protected` nebo `private`, definice by být upravena takto:  
  
```  
public ref class Vector sealed {   
public:  
   property double x {  
      double get() {  
         return _x;  
      }  
  
   private:  
      void set( double newx ) {  
         _x = newx;  
      }  
  
   } // note: extent of private culminates here  
  
// note: dot is a public method of Vector  
double dot( const Vector^ wv );  
  
// etc.  
};  
```  
  
 Obor přístupu klíčového slova v rámci vlastnosti rozšiřuje dokud buď pravé složené závorce vlastnosti nebo specifikace – klíčové slovo další přístup. Nerozšiřuje mimo definici vlastnosti nadřazených úroveň přístupu, ve kterém je definována vlastnost. Ve výše uvedené deklaraci, například `Vector::dot()` je veřejná metoda.  
  
 Zápis sady nebo získat vlastnosti pro tři `Vector` souřadnice zahrnuje tři kroky:  
  
1.  Deklarujte členem privátní stavu příslušného typu.  
  
2.  Vrátí ho, když uživatel chce získat jeho hodnotu.  
  
3.  přiřadí novou hodnotu.  
  
 V nové syntaxe je sdružená vlastnost syntaxi k dispozici který automatizuje tento vzor používání:  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   property double x;   
   property double y;  
   property double z;  
};  
```  
  
 Zajímavé vedlejším účinkem vlastnost syntaxi ve zkráceném tvaru je, že i když se stav backstage je generován kompilátor, není přístupná v rámci třídy s výjimkou prostřednictvím sady nebo získat přístupové objekty.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace členů v rámci třídy nebo rozhraní (C + +/ CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [Vlastnost](../windows/property-cpp-component-extensions.md)