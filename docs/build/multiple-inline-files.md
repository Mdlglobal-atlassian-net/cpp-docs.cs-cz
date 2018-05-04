---
title: Několik vložených souborů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee9be15f029c0aaab3ca4bc47fb183e1499c2e2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="multiple-inline-files"></a>Několik vložených souborů
Příkaz můžete vytvořit více než jeden vloženého souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      command << <<  
inlinetext  
<<[KEEP | NOKEEP]  
inlinetext  
<<[KEEP | NOKEEP]  
```  
  
## <a name="remarks"></a>Poznámky  
 Pro každý soubor zadejte jeden nebo více řádků textu vložené následuje uzavírací řádek obsahující oddělovač. Začněte druhý soubor text na řádek následující rozdělujících řádku pro první soubor.  
  
## <a name="see-also"></a>Viz také  
 [Soubory vložené do souboru pravidel](../build/inline-files-in-a-makefile.md)