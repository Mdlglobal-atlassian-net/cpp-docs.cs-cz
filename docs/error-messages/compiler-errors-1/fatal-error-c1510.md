---
title: Závažná chyba C1510
ms.date: 04/11/2017
f1_keywords:
- C1510
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
ms.openlocfilehash: 33c17a3099f4aed99cc26579d0e65c4a350b4268
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501096"
---
# <a name="fatal-error-c1510"></a>Závažná chyba C1510

Nejde otevřít jazykový prostředek clui. dll.

Kompilátor nemůže načíst knihovnu prostředků jazyka DLL.

Existují dva běžné příčiny tohoto problému. Při použití 32 kompilátorů a nástrojů se tato chyba může zobrazit u velkých projektů, které během propojení používají více než 2 GB paměti. Možné řešení na 64 systémů Windows je 64 použití nativního nativního nebo křížového kompilátoru a nástrojů k vygenerování kódu. To využívá větší místo v paměti dostupné pro 64 aplikace. Pokud je nutné použít 32 kompilátor, protože používáte systém 32, v některých případech můžete zvýšit množství paměti dostupné pro linker do povolenou. Další informace najdete v tématu [optimalizace na 4 gigabajty: Nástroj BCDEdit a Boot.](/windows/win32/memory/4-gigabyte-tuning) ini a příkaz [bcdedit/set increaseuserva](/windows-hardware/drivers/devtest/bcdedit--set)

Další běžnou příčinou je poškozená nebo neúplná instalace sady Visual Studio. V takovém případě znovu spusťte instalační program a opravte nebo přeinstalujte sadu Visual Studio.
