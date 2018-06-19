---
title: Vytvořit vložený Text souboru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ab1154935ac4eb8b0595c84ba8d75a9ca13e4d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367495"
---
# <a name="creating-inline-file-text"></a>Vytvořit vložený text souboru
Vložené soubory jsou trvalé nebo dočasné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      inlinetext  
.  
.  
.  
<<[KEEP | NOKEEP]  
```  
  
## <a name="remarks"></a>Poznámky  
 Zadejte *inlinetext* na první řádek po příkazu. Konec s hranatých závorkách (<<) na začátku samostatném řádku. Tento soubor obsahuje všechny *inlinetext* před rozdělujících závorky. *Inlinetext* může mít makro rozšíření a nahrazení, ale není direktivy nebo makefile komentáře. Mezery, tabulátory a znaky nového řádku jsou považovány oznámena.  
  
 Dočasný soubor existuje po dobu trvání relace a lze opětovně použít další příkazy. Zadejte **zachovat** po uzavírací hranaté závorce úhel zachování soubor po NMAKE relaci; soubor bez názvu se zachová, i na disku s vygenerovaný název souboru. Zadejte **NOKEEP** nebo nic pro dočasný soubor. **ZACHOVAT** a **NOKEEP** nejsou velká a malá písmena.  
  
## <a name="see-also"></a>Viz také  
 [Soubory vložené do souboru pravidel](../build/inline-files-in-a-makefile.md)