---
title: "implementation_only – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: implementation_only
dev_langs: C++
helpviewer_keywords: implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 673fb22feaf53ec4fa018a45c88073e1c04f6c71
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="implementationonly"></a>implementation_only
**Konkrétní C++**  
  
 Potlačí generování hlavičkový soubor .tlh (primární hlavičkový soubor).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
implementation_only  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento soubor obsahuje všechny deklarace, na které se používá ke zveřejnění obsahu knihovny typů. Soubor hlaviček .tli s implementacemi členských funkcí obálky, vygeneruje se se součástí kompilace.  
  
 Pokud tento atribut je zadána, je obsah hlavičky .tli v o stejný obor názvů, který obvykle používají v hlavičce .tlh. Kromě toho nejsou členské funkce deklarované jako vložené.  
  
 `implementation_only` Atribut je určena pro použití ve spojení s [no_implementation –](../preprocessor/no-implementation.md) atribut jako kvůli udržení implementace mimo souborů předkompilovaných hlaviček (PCH). `#import` Příkaz s `no_implementation` atribut je umístěn v oblasti zdroj použít k vytvoření PCH. Výsledný PCH používá několik zdrojových souborů. `#import` Příkaz s `implementation_only` mimo oblast PCH je pak použit atribut. Je nutné použít tento příkaz pouze jednou v jednom ze zdrojové soubory. Tím se vygeneruje všechny požadované obálku členské funkce bez další rekompilace pro každý zdrojový soubor.  
  
> [!NOTE]
>  `implementation_only` Atribut v jednom `#import` příkaz musí být ve spojení s jinou `#import` prohlášení o stejný typ knihovny s `no_implementation` atribut. Chyby kompilátoru, jinak bude vygenerována. Důvodem je, že generované definice tříd obálku `#import` příkaz s `no_implementation` atribut je požadován zkompilovat implementace generovaných `implementation_only` atribut.  
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)