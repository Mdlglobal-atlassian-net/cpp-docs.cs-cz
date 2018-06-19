---
title: Závažná chyba nástroje NMAKE U1033 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1033
dev_langs:
- C++
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1d39d4c35ec66d405d51d601b7c5d2b2ab37b02
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319267"
---
# <a name="nmake-fatal-error-u1033"></a>Závažná chyba nástroje NMAKE U1033
Chyba syntaxe: 'řetězec' neočekávané  
  
 Řetězec není součástí platná syntaxe souboru pravidel.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Pokud sada ukončovací lomené závorky (**<<**) pro vloženého souboru nejsou na začátku řádku, došlo k následující chybě:  
  
    ```  
    syntax error : 'EOF' unexpected  
    ```  
  
2.  Pokud definici makra v soubor pravidel obsažené symbolem rovná (**=**) bez předcházející název nebo pokud definovaný název je makro, které zasahuje do nic, došlo k následující chybě:  
  
    ```  
    syntax error : '=' unexpected  
    ```  
  
3.  Pokud středník (**;**) v řádku komentáře v NÁSTROJÍCH. INI není na začátku řádku, došlo k následující chybě:  
  
    ```  
    syntax error : ';' unexpected  
    ```  
  
4.  Pokud souboru pravidel je formátován pomocí textového editoru, může dojít k následující chybě:  
  
    ```  
    syntax error : ':' unexpected  
    ```