---
title: 'Návod: Sestavení projektu (C++) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 09/14/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- building projects [C++]
- projects [C++], building
- project building [C++]
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5050ab07f430a545e5d2d0497ae2d17b09acdba3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101433"
---
# <a name="walkthrough-building-a-project-c"></a>Návod: Sestavení projektu (C++)
V tomto podrobném návodu se záměrně zavést chybu syntaxe jazyka Visual C++ ve vašem kódu a zjistěte, jak vypadá chyba kompilace a jak ho opravit. Při kompilaci projektu označuje chybová zpráva problém a kde k němu došlo.  
  
## <a name="prerequisites"></a>Požadavky  
  
- Tento názorný průvodce předpokládá, že chápete základy jazyka C++.  
  
- Dále předpokládá, že jste dokončili dříve související návody, které jsou uvedeny v [pomocí integrovaného vývojového prostředí sady Visual Studio pro vývoj v jazyce C++ Desktop](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### <a name="to-fix-compilation-errors"></a>Opravení chyb kompilace  
  
1. V Game.cpp odstraňte středník na posledním řádku tak, aby vypadal takto:  
  
     `return 0`  
  
1. V panelu nabídky zvolte **sestavení** > **sestavit řešení**.  
  
1. Zpráva v **seznam chyb** okno znamená, že došlo k chybě při tvorbě projektu. Popis vypadá zhruba takhle:  
  
     `error C2143: syntax error: missing ';' before '}'`  
  
     Chcete-li zobrazit informace nápovědy o této chybě, zvýrazněte ho v **seznam chyb** okno a klikněte na tlačítko **F1** klíč.  
  
1. Přidejte středník zpět do konce řádku, který obsahuje chybu syntaxe:  
  
     `return 0;`  
  
1. V panelu nabídky zvolte **sestavení** > **sestavit řešení**.  
  
     Zpráva v **výstup** okno znamená, že sestavení projektu zdařilo.  
  
    ```Output  
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------  
    1>Game.cpp  
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe  
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========  
    ```  
  
## <a name="next-steps"></a>Další kroky  

**Předchozí:** [návod: práce s projekty a řešeními (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)<br/>
**Další krok:** [návod: testování projektu (C++)](../ide/walkthrough-testing-a-project-cpp.md)<br/>
  
## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)<br/>
