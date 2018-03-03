---
title: "Vytvořit vložený Text souboru | Microsoft Docs"
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
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dcc27a303e9d03d2e899a76703bcfae5abfd0c04
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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