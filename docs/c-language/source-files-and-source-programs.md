---
title: "Zdrojové soubory a zdrojové programy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- files [C++], source
- programs [C++], source
- source files, specifying in compiler
- source programs
ms.assetid: 18bb2826-17da-48e5-92a2-10e649f1bc9f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8355dd04376e73618a215fa73160dc1ee64dae2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="source-files-and-source-programs"></a>Zdrojové soubory a zdrojové programy
Zdrojový program lze rozdělit do jednoho nebo více „zdrojových souborů“, tzv. „jednotek převodu“. Vstup kompilátoru se nazývá „jednotka převodu“.  
  
## <a name="syntax"></a>Syntaxe  
 *jednotky překladu*:  
 *externí deklarace*  
  
 *jednotky překladu externí – deklarace*  
  
 *externí deklarace*:  
 *definice funkce*  
  
 *deklarace*  
  
 [Přehled deklarací](../c-language/overview-of-declarations.md) dává syntaxe `declaration` nonterminal a *preprocesor odkaz* vysvětluje, jak [překlad jednotky](../preprocessor/phases-of-translation.md) zpracování.  
  
> [!NOTE]
>  V tématu Úvod do [souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md), vysvětlení konvence syntaxe ANSI.  
  
 Součásti jednotky převodu jsou externí deklarace obsahující definice funkcí a deklarace identifikátorů. Tyto deklarace a definice mohou být umístěny ve zdrojových souborech, v souborech hlaviček, v knihovnách i v jiných souborech, které program potřebuje. Pro sestavení programu je zapotřebí každou jednotku převodu zkompilovat a propojit výsledné soubory objektů.  
  
 „Zdrojový program“ jazyka C je kolekcí obecných direktiv, direktiv pragma, deklarací, definicí, bloků příkazů a funkcí. Aby tyto položky byly platnými komponentami programu jazyka Microsoft C, musí být každá z nich zapsána syntaxí popsanou v této knize, přestože se mohou v programu vyskytovat v libovolném pořadí (dle pravidel uvedených v této knize). Umístění těchto komponent v programu ovlivňuje, jak v programu mohou být používány proměnné a funkce. (Viz [doba platnosti, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md) Další informace.)  
  
 Zdrojové soubory nemusí obsahovat spustitelné příkazy. Může být například užitečné umístit definice proměnných do jednoho zdrojového souboru, a potom deklarovat reference na tyto proměnné v jiných zdrojových souborech, které je používají. Tato technika usnadňuje hledání a v případě potřeby také aktualizace definic. Ze stejného důvodu jsou konstanty a makra často uspořádány do samostatných souborů zvaných „vložené soubory“ nebo „soubory hlaviček“, na které lze dle potřeby odkázat ve zdrojových souborech. Najdete v článku *preprocesor odkaz* informace o [makra](../preprocessor/macros-c-cpp.md) a [zahrnout soubory](../preprocessor/hash-include-directive-c-cpp.md).  
  
## <a name="see-also"></a>Viz také  
 [Struktura programu](../c-language/program-structure.md)