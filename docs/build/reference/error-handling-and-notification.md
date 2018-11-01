---
title: Zpracování chyb a oznámení
ms.date: 11/04/2016
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
ms.openlocfilehash: 845a79e035943dbbde0d498702f70ec7dd6b4d3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432390"
---
# <a name="error-handling-and-notification"></a>Zpracování chyb a oznámení

Další informace o zpracování chyb a oznámení, naleznete v tématu [základní informace o funkci pomocné rutiny](understanding-the-helper-function.md).

Další informace o funkce háku najdete v tématu [struktura a definice konstant](../../build/reference/structure-and-constant-definitions.md).

Pokud program používá odloženě zaváděné knihovny DLL, se musí zpracovávají chyby od neošetřené výjimky způsobí selhání, ke kterým je aplikace spuštěna. Zpracování selhání se skládá ze dvou částí:

Obnovení prostřednictvím hák.
Pokud váš kód potřebuje obnovit, nebo alternativní knihovny a/nebo rutiny při selhání, je možné poskytnout hák pomocná funkce, které můžete zadat nebo nápravě. Rutiny musí hook vraťte vhodnou hodnotu, aby se zpracování může pokračovat (HINSTANCE nebo FARPROC) nebo 0, která znamená, že by měl být vyvolána výjimka. Může také vyvolá vlastní výjimky nebo **longjmp** mimo zavěšení. Existují háky oznámení a selhání háků.

Generování sestav prostřednictvím výjimku.
Pokud vše, co je nezbytné pro zpracování chyby pro přerušení postup, je nezbytné žádný háček, tak dlouho, dokud uživatel kód může zpracovávat výjimky.

Následující témata popisují zpracování chyb a oznámení:

- [Háky oznámení](../../build/reference/notification-hooks.md)

- [Selhání háků](../../build/reference/failure-hooks.md)

- [Výjimky](../../build/reference/exceptions-c-cpp.md)

## <a name="see-also"></a>Viz také

[Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)