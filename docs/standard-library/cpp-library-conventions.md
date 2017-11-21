---
title: Konvence knihovny C++ | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- C++ Standard Library, conventions
- classes [C++]
- functions [C++], library naming conventions
- naming conventions [C++], C++ Standard Library
- conventions [C++], C++ Standard Library
- function names [C++]
- coding conventions, C++ Standard Library
- naming conventions [C++], C++ library
ms.assetid: bf41b79a-2d53-4f46-8d05-779358335146
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 67848252bf875303c8120c9d4935e0135f705489
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-library-conventions"></a>Konvence knihovny C++
Knihovna C++ dodržuje mnohem se stejnými názvů jako standardní knihovny jazyka C a navíc několik dalších podle zde uvedeného.  
  
 Implementace má určitá zeměpisnou šířku v tom, jak uvádí typy a funkce v knihovně C++:  
  
-   Názvy funkcí v knihovně standardní C může mít extern #"C++" nebo "C" propojení extern. Zahrnout hlavičku odpovídající standardní C spíše než deklarovat entity vložené knihovny.  
  
-   Název funkce člena třídy knihovny může mít další funkce podpisy přes uvedených v tomto dokumentu. Můžete si být jisti, že volání funkce popsané v tomto poli se chová podle očekávání, ale nelze spolehlivě převzít adresu členské funkce knihovny. (Typ nemusí být očekávat.)  
  
-   Třídy knihovny může mít nedokumentovanými (nevirtuální) základní třídy. Třída zdokumentovaný jako odvozené z jiné třídy, může ve skutečnosti být odvozen od třídy prostřednictvím jiné nedokumentovanými třídy.  
  
-   Typ definovaný jako synonymum pro nějaký typ celé číslo může být stejný jako jeden z několika různých celé číslo.  
  
-   Bitová maska typ se dá implementovat jako typ celé číslo nebo výčet. V obou případech můžete provádět bitové operace (například `AND` a `OR`) na hodnoty stejného typu bitové masky. Elementy `A` a `B` typu bitová maska jsou nenulové hodnoty tak, aby `A`  &  `B` je nulová.  
  
-   Funkce knihovny, která nemá žádné specifikace výjimek může vyvolat výjimku libovolný, pokud jeho definice jasně omezuje tato možnost.  
  
 Na druhé straně platí určitá omezení:  
  
-   Standardní knihovny jazyka C používá makra bez maskování. Jenom určité funkce, které jsou vyhrazené podpisy, nejsou to názvy funkcí sami.  
  
-   Název funkce knihovny mimo třídu nebude mít další, nedokumentovanými, funkce podpisy. Spolehlivě můžete využít svou adresu.  
  
-   Základní třídy a členské funkce označen jako virtuální jsou assuredly virtuální při popsané jako nevirtuální jsou assuredly nevirtuální.  
  
-   Dva typy určené knihovně C++ se liší vždy, není-li tento dokument explicitně navrhuje jinak.  
  
-   Funkce Knihovna, včetně výchozí verze replaceable funkce, můžete vyvolat *maximálně* tyto výjimky uvedené v všechny specifikace výjimek. Žádné destruktory knihovna generování výjimek. Funkce standardní knihovny jazyka C může rozšířit výjimku, jako když `qsort` volání funkce porovnání, který vyvolá výjimku, ale není jinak vyvolají výjimky.  
  
## <a name="see-also"></a>Viz také  
 [Přehled knihovny C++ Standard](../standard-library/cpp-standard-library-overview.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

