---
title: "Nastavení možností Linkeru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- files [C++], LINK
- input files [C++], linker
- linker [C++], ways to set options
- linker [C++], switches
- input files [C++]
- object/library modules
ms.assetid: e08fb487-0f2e-4f24-87db-232dbc8bd2e2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ba42921f1e192c90e302b437b9a7d1b4e5eb34e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="setting-linker-options"></a>Nastavení možností linkeru
Možnosti linkeru můžete nastavit, uvnitř nebo vně vývojového prostředí. Téma pro jednotlivé možnosti linkeru popisuje, jak lze nastavit ve vývojovém prostředí. V tématu [možnosti Linkeru](../../build/reference/linker-options.md) úplný seznam.  
  
 Když spustíte odkaz mimo vývojového prostředí, můžete určit vstup jeden nebo více způsoby:  
  
-   Na [příkazového řádku](../../build/reference/linker-command-line-syntax.md)  
  
-   Pomocí [soubory příkazů](../../build/reference/link-command-files.md)  
  
-   V [proměnné prostředí](../../build/reference/link-environment-variables.md)  
  
 První možnosti procesy odkazů určeném v proměnné prostředí odkaz, podle instrukcí v pořadí, jsou uvedené v příkazovém řádku a soubory příkazů. Pokud se možnost opakuje s jinou argumenty, byl naposledy zpracovat přednost.  
  
 Možnosti se vztahují na celou sestavení; žádné možnosti je použít pro konkrétní vstupní soubory.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz sestavení C/C++](../../build/reference/c-cpp-building-reference.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)