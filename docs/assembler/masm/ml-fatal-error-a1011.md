---
title: Závažná chyba nástroje ML A1011 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1011
dev_langs:
- C++
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 843d676cba61e0da5f917a48408e56e79abb9efd
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057199"
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
  
-   [. ELSE](../../assembler/masm/dot-else.md) následující `.ELSE`  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)