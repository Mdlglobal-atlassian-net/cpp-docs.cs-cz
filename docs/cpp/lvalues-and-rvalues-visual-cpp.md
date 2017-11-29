---
title: 'Hodnotu kategorie: Hodnoty lvalue a rvalue (Visual C++) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 34513ba6799b1f70d16867571d38185420fa3576
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="lvalues-and-rvalues-visual-c"></a>Hodnoty lvalue a rvalue (Visual C++)
Každý výraz C++ má typ a patří k *hodnota kategorie*. Hodnota kategorie jsou základem pro pravidla, která řídí kompilátory při vytváření, kopírování a přesouvání dočasné objekty při vyhodnocení výrazu. 

 C ++ 17 standardní definuje kategorie hodnota výrazu následujícím způsobem:

- A *glvalue* je výraz, jehož vyhodnocení určuje identitu objektu, bitová pole nebo funkce. 
- A *prvalue* je výraz, jehož vyhodnocení inicializuje objekt nebo pole bit nebo vypočítá hodnotu operand operátoru, podle určeného kontextu, ve kterém it se zobrazí. 
- *Xvalue* je glvalue, který označuje na objekt nebo pole bit, jejichž prostředky lze opětovně použít (obvykle protože je u konce své životnosti). [Příklad: osa x, hodnoty, například volání funkce s návratovým typem je odkaz rvalue nebo přetypování na typ deklarátor odkazu poskytne určité druhy výrazů zahrnující odkazy rvalue (8.3.2). ] 
- *Lvalue* je glvalue, který není hodnotu xvalue. 
- *Rvalue* prvalue nebo hodnotu xvalue. 

Následující diagram znázorňuje vztahy mezi kategorií:

 ![Kategorie hodnota výrazů C++](media/value_categories.png "kategorie hodnota výrazů C++")  
 
 Lvalue má adresu, která můžete přístup k vaší aplikaci. Příklady výrazů lvalue názvy proměnných, včetně `const` proměnné, elementy pole funkce volání, které vracejí odkazu lvalue, bitových polí, sjednocení a členy třídy. 
 
 Výraz prvalue nemá žádnou adresu, která je přístupná pomocí vašeho programu. Příklady výrazů prvalue: literály, volání funkce, která návratový typ – referenční dokumentace a dočasné objekty, které jsou vytvořené během evalution výraz, ale přístupné pouze pomocí kompilátoru. 

 Výraz hodnotu xvalue nemá žádnou adresu, ale lze ji použít k chybě při inicializaci deklarátor odkazu, který poskytuje přístup k výrazu. Příklady zahrnují volání funkcí, které vrátí deklarátor odkazu a dolní index pole, člen a ukazatele na člena výrazy kde objekt nebo pole je deklarátor odkazu. 
 
 Následující příklad ukazuje několik správných a nesprávných použití l-hodnot a r-hodnot:  
  
```  
// lvalues_and_rvalues2.cpp  
int main()  
{  
   int i, j, *p;  
  
   // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.  
   i = 7;  
  
   // Incorrect usage: The left operand must be an lvalue (C2106).  `j * 4` is a prvalue.
   7 = i; // C2106  
   j * 4 = 7; // C2106  
  
   // Correct usage: the dereferenced pointer is an lvalue.  
   *p = i;   
  
   const int ci = 7;  
   // Incorrect usage: the variable is a non-modifiable lvalue (C3892).  
   ci = 9; // C3892  
  
   // Correct usage: the conditional operator returns an lvalue.  
   ((i < 3) ? i : j) = 7;  
}  
```  
  
> [!NOTE]
>  Příklady v tomto tématu ukazují správné a nesprávné použití v případě, že operátory nejsou přetíženy. Přetěžováním operátorů lze vytvořit výraz jako l-hodnotu `j * 4`.  

  
 Podmínky *lvalue* a *rvalue* se často používají při odkazu na odkazy na objekty. Další informace naleznete v tématu [deklarátor odkazu Lvalue: &](../cpp/lvalue-reference-declarator-amp.md) a [Rvalue – deklarátor odkazu: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="see-also"></a>Viz také  
 [Základní koncepty](../cpp/basic-concepts-cpp.md)   
 [Deklarátor odkazu lvalue: &](../cpp/lvalue-reference-declarator-amp.md)   
 [Deklarátor odkazu rvalue: & &](../cpp/rvalue-reference-declarator-amp-amp.md)