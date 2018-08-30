---
title: Diagnostika vytištěná podle funkce assert | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e824e94f79aa01ab3a82675fb3e8f76059c567d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195549"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostika vytištěná podle funkce assert
**ANSI 4.2** diagnostické zprávy vytištěné funkcí a její chování **vyhodnocení** – funkce  
  
**Vyhodnocení** funkce vytiskne diagnostickou zprávu a zavolá **přerušit** rutině, pokud je výraz nepravdivý (0). Diagnostická zpráva má tvar  

> **Chyba kontrolního výrazu**: <em>výraz</em>**, soubor** <em>filename</em>**, řádek** *číslo řádku*  

kde *filename* je název zdrojového souboru a *linenumber* je číslo řádku výrazu, který se ve zdrojovém souboru se nezdařilo. Pokud nebyla provedena žádná akce *výraz* hodnotu true (nenulovou).  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny](../c-language/library-functions.md)