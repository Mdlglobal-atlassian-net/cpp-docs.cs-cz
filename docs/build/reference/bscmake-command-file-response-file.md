---
title: Soubor příkazů BSCMAKE (soubor odezvy) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a879306078c52e0ad11d29f1786a2e55c2480d2f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369562"
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