---
title: Závažná chyba C1060
ms.date: 11/04/2016
f1_keywords:
- C1060
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
ms.openlocfilehash: 83135b77ceb75b4c2b05211260d1aed8fac6777f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320281"
---
# <a name="fatal-error-c1060"></a>Závažná chyba C1060

kompilátor je mimo místo haldy

Operační systém nebo knihovna run-time nemůže vyplnit požadavek na paměť.

### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>Chcete-li tuto chybu opravit, vyzkoušejte následující možná řešení

1. Pokud kompilátor také problémy chyby [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) a [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md), použijte [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) kompilátor možnost snížit limit přidělení paměti. Více místa haldy je k dispozici pro vaši aplikaci, pokud snížíte zbývající přidělení paměti.

   Pokud je možnost [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) již nastavena, zkuste ji odebrat. Místo haldy může být vyčerpáno, protože limit přidělení paměti zadaný v možnosti je příliš vysoký. Kompilátor používá výchozí limit, pokud odeberete možnost [/Zm.](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)

1. Pokud sestavujete na 64bitové platformě, použijte 64bitovou sadu nástrojů kompilátoru. Další informace naleznete v [tématu Postup: Povolení 64bitové sady nástrojů Visual C++ na příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. V 32bitovém systému Windows zkuste použít přepínač [/3GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) boot.ini.

1. Zvětšete velikost odkládacího souboru systému Windows.

1. Zavřete ostatní spuštěné programy.

1. Odstraňte nepotřebné vkládané soubory.

1. Eliminujte například zbytečné globální proměnné dynamickým přidělováním paměti namísto deklarování velkého pole.

1. Odstraňte nepoužité deklarace.

1. Aktuální soubor rozdělte na menší soubory.
