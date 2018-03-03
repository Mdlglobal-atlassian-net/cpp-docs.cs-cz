---
title: "Soubor příkazů BSCMAKE (soubor odezvy) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c250af9f1af96bb051be0b2cd347ecd8d98d809
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 [BSCMAKE – referenční dokumentace](../../build/reference/bscmake-reference.md)