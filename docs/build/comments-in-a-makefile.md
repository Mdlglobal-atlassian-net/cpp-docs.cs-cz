---
title: Komentáře v souboru pravidel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- makefiles, comments
ms.assetid: 76fd9e3d-5966-47f4-a091-c9e80b232b49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e404f3fffd0176e63a2df89d4d879bfba07f7093
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="comments-in-a-makefile"></a>Komentáře v souboru pravidel
Předcházet komentář znakem čísla (#). NMAKE ignoruje text z znaménko čísla na další znak nového řádku. Příklady:  
  
```  
# Comment on line by itself  
OPTIONS = /MAP  # Comment on macro definition line  
  
all.exe : one.obj two.obj  # Comment on dependency line  
    link one.obj two.obj  
# Comment in commands block  
#   copy *.obj \objects  # Command turned into comment  
    copy one.exe \release  
  
.obj.exe:  # Comment on inference rule line  
    link $<  
  
my.exe : my.obj ; link my.obj  # Err: cannot comment this  
 # Error: # must be the first character  
.obj.exe: ; link $<  # Error: cannot comment this  
```  
  
 Pokud chcete zadat literálu znaménko čísla, ji předchází šipka nahoru (**^**), a to takto:  
  
```  
DEF = ^#define  #Macro for a C preprocessing directive  
```  
  
## <a name="see-also"></a>Viz také  
 [Obsah souboru pravidel](../build/contents-of-a-makefile.md)