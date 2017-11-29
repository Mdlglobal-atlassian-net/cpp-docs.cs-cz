---
title: "Závažná chyba nástroje ML A1011 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A1011
dev_langs: C++
helpviewer_keywords: A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 686ae83c4316caee243750a6ed1c28303c9de0ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ml-fatal-error-a1011"></a>Závažná chyba nástroje ML A1011
**Direktiva musí být v bloku ovládací prvek**  
  
 Assembleru najít direktivu vysoké úrovně nebyla očekávána jen jedna. Jeden z následujících direktivy nebyl nalezen:  
  
-   [. ELSE](../../assembler/masm/dot-else.md) bez [. POKUD](../../assembler/masm/dot-if.md)  
  
-   [. ENDIF](../../assembler/masm/dot-endif.md) bez [. POKUD](../../assembler/masm/dot-if.md)  
  
-   [. ENDW](../../assembler/masm/dot-endw.md) bez [. CHVÍLI](../../assembler/masm/dot-while.md)  
  
-   [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md) bez [. OPAKOVAT](../../assembler/masm/dot-repeat.md)  
  
-   [. Pokračovat](../../assembler/masm/dot-continue.md) bez [. Při](../../assembler/masm/dot-while.md) nebo [. OPAKOVAT](../../assembler/masm/dot-repeat.md)  
  
-   [. ROZDĚLIT](../../assembler/masm/dot-break.md) bez [. Při](../../assembler/masm/dot-while.md) nebo [. OPAKOVAT](../../assembler/masm/dot-repeat.md)  
  
-   [. ELSE](../../assembler/masm/dot-else.md) následující`.ELSE`  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy nástroje ML](../../assembler/masm/ml-error-messages.md)