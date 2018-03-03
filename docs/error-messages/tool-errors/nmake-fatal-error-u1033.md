---
title: "Závažná chyba nástroje NMAKE U1033 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1033
dev_langs:
- C++
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 94f2626e1ce318d83d306595e386f880c62dec3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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