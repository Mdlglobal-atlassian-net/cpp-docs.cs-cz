---
title: "Kompilátoru (úroveň 1) upozornění C4657 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4657
dev_langs: C++
helpviewer_keywords: C4657
ms.assetid: eb750050-cea6-4ead-b80c-d5dcd4971cfc
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cfe2a392de655fdc5340f22784fcd5763e79ff56
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4657"></a>C4657 kompilátoru upozornění (úroveň 1)
výraz zahrnuje datový typ, který je nového od poslední sestavení  
  
 Přidat nebo změnit datový typ, což nové ke zdrojovému kódu od poslední úspěšné sestavení. Upravit a pokračovat nepodporuje změny existující datové typy.  
  
 Toto upozornění bude vždy následovat [závažná chyba C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Další informace najdete v tématu [podporované změny kódu](/visualstudio/debugger/supported-code-changes-cpp).  
  
### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Chcete-li odebrat toto upozornění bez ukončení aktuální relaci ladění  
  
1.  Změna datového typu zpět do stavu před chyba.  
  
2.  Z **ladění** nabídce zvolte **použít změny kódu**.  
  
### <a name="to-remove-this-error-without-changing-your-source-code"></a>Chcete-li odebrat tuto chybu beze změny vašeho zdrojového kódu  
  
1.  Z **ladění** nabídce zvolte **Zastavte ladění**.  
  
2.  Z **sestavení** nabídce zvolte **sestavení**.