---
title: Zdrojové soubory a zdrojové programy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- files [C++], source
- programs [C++], source
- source files, specifying in compiler
- source programs
ms.assetid: 18bb2826-17da-48e5-92a2-10e649f1bc9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5189f1e9467977afda919862005901a633dae6a7
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765158"
---
# <a name="source-files-and-source-programs"></a>Zdrojové soubory a zdrojové programy
Zdrojový program lze rozdělit do jednoho nebo více „zdrojových souborů“, tzv. „jednotek převodu“. Vstup kompilátoru se nazývá „jednotka převodu“.  
  
## <a name="syntax"></a>Syntaxe

*translation-unit*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*externí deklarace* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jednotka překladu* *externí deklarace*  
  
*externí deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*definice funkce*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace*

[Přehled deklarací](../c-language/overview-of-declarations.md) poskytuje syntaxi `declaration` neterminálu a *odkazu preprocesoru* vysvětluje, jak [jednotce překladu](../preprocessor/phases-of-translation.md) se zpracovává.  
  
> [!NOTE]
>  Naleznete v úvodu do [souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md), vysvětlení konvencí syntaxe standardu ANSI.  
  
Součásti jednotky převodu jsou externí deklarace obsahující definice funkcí a deklarace identifikátorů. Tyto deklarace a definice mohou být umístěny ve zdrojových souborech, v souborech hlaviček, v knihovnách i v jiných souborech, které program potřebuje. Pro sestavení programu je zapotřebí každou jednotku převodu zkompilovat a propojit výsledné soubory objektů.  
  
„Zdrojový program“ jazyka C je kolekcí obecných direktiv, direktiv pragma, deklarací, definicí, bloků příkazů a funkcí. Aby tyto položky byly platnými komponentami programu jazyka Microsoft C, musí být každá z nich zapsána syntaxí popsanou v této knize, přestože se mohou v programu vyskytovat v libovolném pořadí (dle pravidel uvedených v této knize). Umístění těchto komponent v programu ovlivňuje, jak v programu mohou být používány proměnné a funkce. (Viz [životnost, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md) Další informace.)  
  
Zdrojové soubory nemusí obsahovat spustitelné příkazy. Může být například užitečné umístit definice proměnných do jednoho zdrojového souboru, a potom deklarovat reference na tyto proměnné v jiných zdrojových souborech, které je používají. Tato technika usnadňuje hledání a v případě potřeby také aktualizace definic. Ze stejného důvodu jsou konstanty a makra často uspořádány do samostatných souborů zvaných „vložené soubory“ nebo „soubory hlaviček“, na které lze dle potřeby odkázat ve zdrojových souborech. Zobrazit *odkazu preprocesoru* informace o [makra](../preprocessor/macros-c-cpp.md) a [soubory k zahrnutí](../preprocessor/hash-include-directive-c-cpp.md).  
  
## <a name="see-also"></a>Viz také  
[Struktura programu](../c-language/program-structure.md)