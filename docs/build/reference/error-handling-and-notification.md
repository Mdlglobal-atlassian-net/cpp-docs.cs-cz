---
title: Zpracování chyb a oznámení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 738721eb3fc37ba076157129cb88a22f2c90e464
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="error-handling-and-notification"></a>Zpracování chyb a oznámení
Další informace o zpracování chyb a oznámení najdete v tématu [pochopení pomocné funkce](understanding-the-helper-function.md).  
  
 Další informace o funkce háku najdete v tématu [struktura a definice konstant](../../build/reference/structure-and-constant-definitions.md).  
  
 Pokud vaše aplikace používá knihovny DLL s odloženým načtením, se musí zpracovávají chyby vzhledem k tomu, ke kterým dochází při spuštění programu bude výsledkem neošetřených výjimek. Zpracování selhání se skládá ze dvou částí:  
  
 Obnovení prostřednictvím háku.  
 Pokud váš kód potřebujete obnovit nebo zadejte alternativní knihovny nebo rutiny při selhání, háku lze zadat pomocné funkce, která můžete zadat nebo nápravě. Běžné potřeby háku vrátit vhodnou hodnotu tak, aby zpracování může pokračovat (HINSTANCE nebo FARPROC), nebo 0 k označení, že by měl být vyvolána výjimka. Také ho může vyvolat svou vlastní výjimku nebo **longjmp** mimo hák. Existují háky oznámení a selhání háků.  
  
 Generování sestav prostřednictvím výjimku.  
 Pokud všechny, které jsou nezbytné pro zpracování chyby na zrušení postup, je nutné žádné háku, tak dlouho, dokud uživatelského kódu může zpracovat výjimku.  
  
 Následující témata popisují zpracování chyb a oznámení:  
  
-   [Háky oznámení](../../build/reference/notification-hooks.md)  
  
-   [Selhání háků](../../build/reference/failure-hooks.md)  
  
-   [Výjimky](../../build/reference/exceptions-c-cpp.md)  
  
## <a name="see-also"></a>Viz také  
 [Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)