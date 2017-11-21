---
title: "Inicializace řetězců | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- character arrays, initializing
- strings [C++], initializing
- initializing arrays, strings
ms.assetid: 0ab8079d-d0d3-48f9-afd1-36a7bb439b29
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 830e959e8cd9e57745d08da3d4184fbe11a5bb6a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="initializing-strings"></a>Inicializace řetězců
Pole znaků (nebo širokých znaků) lze inicializovat textovým literálem (nebo širokým textovým literálem). Příklad:  
  
```  
char code[ ] = "abc";  
```  
  
 inicializuje pole `code` jako pole znaků o čtyřech prvcích. Čtvrtý prvek je znak Null, který ukončuje všechny textové literály.  
  
 Seznam identifikátorů může dosahovat maximálně délky počtu identifikátorů, které mají být inicializovány. Zadáte-li velikost pole menší než řetězec, jsou přesahující znaky ignorovány. Například následující deklarace inicializuje pole `code` jako pole znaků o třech prvcích:  
  
```  
char code[3] = "abcd";  
```  
  
 Do pole `code` jsou přiřazeny pouze první tři znaky inicializátoru. Znak `d` a znak Null ukončující řetězec jsou ignorovány. Tím dojde k vytvoření neukončeného řetězce (tedy řetězce bez hodnoty 0 označující jeho konec) a k vygenerování diagnostické zprávy, která tuto situaci oznamuje.  
  
 Deklarace  
  
```  
char s[] = "abc", t[3] = "abc";  
```  
  
 je shodná s  
  
```  
char s[]  = {'a', 'b', 'c', '\0'},   
     t[3] = {'a', 'b', 'c' };  
```  
  
 Je-li řetězec kratší než zadaná velikost pole, jsou zbývající prvky pole inicializovány na hodnotu 0.  
  
 **Konkrétní Microsoft**  
  
 V jazyce Microsoft C mohou být textové literály dlouhé až 2048 bajtů.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Inicializace](../c-language/initialization.md)