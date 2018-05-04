---
title: C deklarace a definice | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 575f0c9b-5554-4346-be64-b2129ca9227f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c459999ab902a2498d4ffe4cc2d437a0a432b9b7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="c-declarations-and-definitions"></a>Deklarace a definice jazyka C
„Deklarace“ vytvoří přidružení mezi určitou proměnnou, funkcí nebo typem a jejich atributy. [Přehled deklarací](../c-language/overview-of-declarations.md) dává ANSI syntaxe `declaration` nonterminal. Deklarace také určuje, kdy a kde lze k identifikátoru přistupovat („propojení“ identifikátoru). V tématu [doba platnosti, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md) informace o propojení.  
  
 „Definice“ proměnné vytváří stejné přidružení jako deklarace, ale také způsobí přiřazení úložiště proměnné.  
  
 Například funkce `main`, `find` a `count` a proměnné `var` a `val` jsou definovány v jednom zdrojovém souboru v tomto pořadí:  
  
```  
int main() {}  
  
int var = 0;  
double val[MAXVAL];  
char find( fileptr ) {}  
int count( double f ) {}  
```  
  
 Proměnné `var` a `val` lze použít ve funkcích `find` a `count` a nejsou požadovány žádné další deklarace. Ale tyto názvy nejsou ve funkci `main` viditelné (přístupné).  
  
## <a name="see-also"></a>Viz také  
 [Zdrojové soubory a zdrojové programy](../c-language/source-files-and-source-programs.md)