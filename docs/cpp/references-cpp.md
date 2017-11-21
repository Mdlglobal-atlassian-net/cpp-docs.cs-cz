---
title: Odkazy (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- objects [C++], referencing
- references [C++]
- references, to pointers
- declarations, references
- references, declaring
- referencing objects, declarator syntax
ms.assetid: 68156f7f-97a0-4b66-b26d-b25ade5e3bd8
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4178d9d6a48e10510bb739bc2e1a55ecbe2714e5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="references-c"></a>Odkazy (C++)
Odkaz, jako je ukazatel, ukládá adresu objektu, který se nachází na jiném místě v paměti. Na rozdíl od ukazatele, nelze vytvořit odkaz po inicializaci k odkazovat na jiný objekt, nebo nastavte na hodnotu null. Existují dva druhy odkazy: lvalue odkazy, které se týkají pojmenované proměnnou a rvalue odkazy, které se vztahují [dočasný objekt](../cpp/temporary-objects.md). & Operátor označuje, že odkazu lvalue a & & – operátor označuje deklarátor odkazu nebo universal odkaz (rvalue nebo lvalue) v závislosti na kontextu.  
  
 Odkazy mohou být deklarován pomocí následující syntaxe:  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers   
[ms-modifier] declarator [= expression];  
```  
  
 Mohou být použity žádné platné deklarátor zadání odkaz. Pokud je odkaz odkaz na typ funkce nebo pole, platí následující zjednodušenou syntaxi:  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers [& or &&]   
[cv-qualifiers] identifier [= expression];  
```  
  
 Odkazy jsou deklarovány následujícím způsobem:  
  
 1. Specifikátory deklarace:  
  
-   Specifikátor třídy úložiště volitelné.  
  
-   Volitelné **const** nebo `volatile` kvalifikátory.  
  
-   Specifikátor typu: název typu.  
  
-   2. Deklarátor:  
  
-   Volitelné Microsoft konkrétní modifikátor. Další informace najdete v tématu [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
-   & Operátor nebo & & – operátor.  
  
-   Volitelné **const** nebo `volatile` qualifers.  
  
-   Identifikátor.  
  
 3. Inicializátoru volitelné.  
  
 Složitější formuláře deklarátor ukazatele na pole a funkce se rovněž vztahují na odkazy na pole a funkce, najdete v části [ukazatele](../cpp/pointers-cpp.md) a [deklarátory](http://msdn.microsoft.com/en-us/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838).  
  
 Více deklarátor a inicializátory mohou objevit v následujících jediné deklaraci specifikátor čárkami oddělený seznam. Příklad:  
  
```  
int &i;   
int &i, &j;   
```  
  
 Odkazy, ukazatelů a objektů může deklarovat společně:  
  
```  
int &ref, *ptr, k;   
```  
  
 Odkaz na adresu objektu, ale syntakticky chová jako objekt.  
  
 V následující program, Všimněte si, že název objektu, `Today`a odkaz na objekt, `TodayRef`, je možné stejně jako v aplikacích:  
  
## <a name="example"></a>Příklad  
  
```  
// references.cpp  
#include <stdio.h>  
struct S {  
   short i;  
};  
  
int main() {  
   S  s;   // Declare the object.  
   S& SRef = s;   // Declare the reference.  
   s.i = 3;  
  
   printf_s("%d\n", s.i);  
   printf_s("%d\n", SRef.i);  
  
   SRef.i = 4;  
   printf_s("%d\n", s.i);  
   printf_s("%d\n", SRef.i);  
}  
```  
  
```Output  
3  
3  
4  
4  
```  
  
## <a name="comment"></a>Komentář  
 Témata v této části:  
  
-   [Argumenty funkce typu odkazu](../cpp/reference-type-function-arguments.md)  
  
-   [Vrácení funkce typu odkazu](../cpp/reference-type-function-returns.md)  
  
-   [Odkazy na ukazatele](../cpp/references-to-pointers.md)  
  
