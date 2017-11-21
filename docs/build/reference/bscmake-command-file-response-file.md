---
title: "Soubor příkazů BSCMAKE (soubor odezvy) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1d5dd2696a48a84672350b90b569c8f0caf7c3cd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="bscmake-command-file-response-file"></a>Soubor příkazů BSCMAKE (soubor odezvy)
Můžete zadat část nebo všechny z příkazového řádku vstup v soubor příkazů. Zadejte soubor příkazů pomocí následující syntaxe:  
  
```  
BSCMAKE @filename  
```  
  
 Je povolen pouze jeden příkaz soubor. Můžete zadat cestu s *filename*. Předcházet *filename* s znaku zavináče (@). BSCMAKE nepředpokládá rozšíření. Můžete zadat další *sbrfiles* na příkazovém řádku po *filename*. Příkaz Soubor je textový soubor, který obsahuje vstup BSCMAKE ve stejném pořadí, jako by ji zadejte na příkazovém řádku. Argumenty příkazového řádku oddělte jeden nebo více mezery, tabulátory nebo znaky nového řádku.  
  
 Následující příkaz volá BSCMAKE pomocí příkazového řádku:  
  
```  
BSCMAKE @prog1.txt  
```  
  
 Toto je ukázkový soubor příkaz:  
  
```  
/n /v /o main.bsc /El  
/S (  
toolbox.h  
verdate.h c:\src\inc\screen.h  
)  
file1.sbr file2.sbr file3.sbr file4.sbr  
```  
  
## <a name="see-also"></a>Viz také  
 [BscMake – odkaz](../../build/reference/bscmake-reference.md)