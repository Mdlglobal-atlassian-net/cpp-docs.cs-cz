---
title: "Literál zřetězení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- concatenating strings
- strings [C++], concatenating
ms.assetid: 51486b1f-4b1e-4061-9add-1aa38c6cdb3c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5974e192e32c612fe995cbc736e703f6168a3e8d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="string-literal-concatenation"></a>Zřetězení textového literálu
Chcete-li vytvořit textové literály, které zabírají více než jeden řádek, lze dva řetězce zřetězit. Chcete-li to provést, zadejte zpětné lomítko a poté stiskněte klávesu RETURN. Zpětné lomítko způsobí, že kompilátor bude ignorovat následující znak nového řádku. Například textový literál  
  
```  
"Long strings can be bro\  
ken into two or more pieces."  
```  
  
 je stejný jako řetězec  
  
```  
"Long strings can be broken into two or more pieces."  
```  
  
 Zřetězení řetězců lze použít kdekoli tam, kde jste dříve použili zpětné lomítko následované znakem nového řádku pro zadání řetězců delších než jeden řádek.  
  
 Chcete-li vynutit nový řádek v řetězci literálu, zadejte nový řádek řídicí sekvence (**\n**) v bodě v řetězci, kam chcete řádku porušené, následujícím způsobem:  
  
```  
"Enter a number between 1 and 100\nOr press Return"  
```  
  
 Protože řetězce mohou začínat na jakémkoli sloupci zdrojového kódu a dlouhé řetězce mohou pokračovat na jakémkoli sloupci následujícího řádku, umístěním řetězců lze vylepšit čitelnost zdrojového kódu. V obou případech není jejich reprezentace na obrazovce při výstupu ovlivněna. Příklad:  
  
```  
printf_s ( "This is the first half of the string, "  
           "this is the second half ") ;  
```  
  
 Pokud je každá část řetězce uzavřená v uvozovkách, jsou tyto části zřetězeny a na výstupu jsou jako jeden řetězec. Tento zřetězení k podle pořadí událostí dojde během kompilace určeného [fáze překladu](../preprocessor/phases-of-translation.md).  
  
```  
"This is the first half of the string, this is the second half"  
```  
  
 Řetězec ukazatel, inicializovat jako dvě odlišné textové literály oddělených jenom prázdné znaky, je uložený jako jeden řetězec (ukazatele jsou popsané v [deklarace ukazatelů](../c-language/pointer-declarations.md)). Při správném odkazování je výsledek v následujícím příkladu stejný jako v předchozím příkladu:  
  
```  
char *string = "This is the first half of the string, "  
               "this is the second half";  
  
printf_s( "%s" , string ) ;  
```  
  
 Ve fázi překladu 6 jsou vícebajtové znakové sekvence určené libovolnou sekvencí sousedních textových literálů nebo sousedních literálů širokých řetězců zřetězeny do jediné vícebajtové sekvence znaků. Proto nenavrhujte programy umožňující změnu textových literálů během provádění. Standard ANSI jazyka C určuje, že výsledek změny řetězce není definován.  
  
## <a name="see-also"></a>Viz také  
 [Textové literály jazyka C](../c-language/c-string-literals.md)