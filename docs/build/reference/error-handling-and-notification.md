---
title: Zpracování chyb a oznámení
ms.date: 11/04/2016
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
ms.openlocfilehash: 29fe46e15712609ec0c4f268749aaefed103117e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812938"
---
# <a name="error-handling-and-notification"></a>Zpracování chyb a oznámení

Další informace o zpracování chyb a oznámení, naleznete v tématu [základní informace o funkci pomocné rutiny](understanding-the-helper-function.md).

Další informace o funkce háku najdete v tématu [struktura a definice konstant](structure-and-constant-definitions.md).

Pokud program používá odloženě zaváděné knihovny DLL, se musí zpracovávají chyby od neošetřené výjimky způsobí selhání, ke kterým je aplikace spuštěna. Zpracování selhání se skládá ze dvou částí:

Obnovení prostřednictvím hák.
Pokud váš kód potřebuje obnovit, nebo alternativní knihovny a/nebo rutiny při selhání, je možné poskytnout hák pomocná funkce, které můžete zadat nebo nápravě. Rutiny musí hook vraťte vhodnou hodnotu, aby se zpracování může pokračovat (HINSTANCE nebo FARPROC) nebo 0, která znamená, že by měl být vyvolána výjimka. Může také vyvolá vlastní výjimky nebo **longjmp** mimo zavěšení. Existují háky oznámení a selhání háků.

Generování sestav prostřednictvím výjimku.
Pokud vše, co je nezbytné pro zpracování chyby pro přerušení postup, je nezbytné žádný háček, tak dlouho, dokud uživatel kód může zpracovávat výjimky.

Následující témata popisují zpracování chyb a oznámení:

- [Háky oznámení](notification-hooks.md)

- [Selhání háků](failure-hooks.md)

- [Výjimky](exceptions-c-cpp.md)

## <a name="see-also"></a>Viz také:

[Podpora linkeru pro knihovny DLL s odloženým načtením](linker-support-for-delay-loaded-dlls.md)
