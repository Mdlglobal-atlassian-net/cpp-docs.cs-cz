---
title: "Kompilátoru (úroveň 1) upozornění C4655 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4655
dev_langs: C++
helpviewer_keywords: C4655
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 891fe3c68e93defba011d4ad4c90daf25fe3a799
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4655"></a>C4655 kompilátoru upozornění (úroveň 1)
**'**   
 ***symbol* ': typ proměnné je nového od poslední sestavení nebo je definován jinak jinde**  
  
 Změnit nebo přidat nový typ dat od poslední úspěšné sestavení. Upravit a pokračovat nepodporuje změny existující datové typy.  
  
 Toto upozornění je následován [závažná chyba C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Další informace najdete v tématu [podporované změny kódu](/visualstudio/debugger/supported-code-changes-cpp).  
  
### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Chcete-li odebrat toto upozornění bez ukončení aktuální relaci ladění  
  
1.  Změna datového typu zpět do stavu před chyba.  
  
2.  Z **ladění** nabídce zvolte **použít změny kódu**.  
  
### <a name="to-remove-this-warning-without-changing-your-source-code"></a>Chcete-li odebrat toto upozornění beze změny vašeho zdrojového kódu  
  
1.  Z **ladění** nabídce zvolte **Zastavte ladění**.  
  
2.  Z **sestavení** nabídce zvolte **sestavení**.