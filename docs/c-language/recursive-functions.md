---
title: "Rekurzivní funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C], recursive
- function calls, recursive
- functions [C], calling recursively
- recursive function calls
ms.assetid: 59739040-3081-4006-abbc-9d8423992bce
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cca28b41b15ae14504ac5692a3e8a7063a11e862
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="recursive-functions"></a>Rekurzivní funkce
Všechny funkce v programu jazyka C lze volat rekurzivně, což znamená, že volají samy sebe. Počet rekurzivních volání je omezen velikostí zásobníku. Najdete v článku [/STACK (přidělení zásobníku)](../build/reference/stack-stack-allocations.md) (/ STACK) – možnost linkeru informace o linkeru možnosti tohoto nastavení velikosti zásobníku. Pokaždé, když je volána funkce, nové úložiště je přidělen pro parametry a **automaticky** a **zaregistrovat** proměnné tak, aby se jejich hodnoty v předchozí, nedokončené volání nepřepíšou. Parametry jsou přímo přístupné pouze instanci funkce, ve které jsou vytvořeny. Předchozí parametry nejsou následné instanci funkce přímo přístupné.  
  
 Všimněte si, že proměnné deklarovány s **statické** úložiště nevyžadují nové úložiště s každou rekurzivní volání. Jejich úložiště existuje po dobu životnosti programu. Každý odkaz na takovou proměnnou přistupuje do stejné oblasti úložiště.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje rekurzivní volání:  
  
```  
int factorial( int num );      /* Function prototype */  
  
int main()  
{  
    int result, number;  
    .  
    .  
    .  
    result = factorial( number );  
}  
  
int factorial( int num )      /* Function definition */  
{  
    .  
    .  
    .  
    if ( ( num > 0 ) || ( num <= 10 ) )  
        return( num * factorial( num - 1 ) );  
}  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Volání funkcí](../c-language/function-calls.md)