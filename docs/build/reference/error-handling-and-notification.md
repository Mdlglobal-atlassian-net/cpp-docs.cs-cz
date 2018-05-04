---
title: Zpracování chyb a oznámení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2edec23da89766a45545566b0a689001d3ca75f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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