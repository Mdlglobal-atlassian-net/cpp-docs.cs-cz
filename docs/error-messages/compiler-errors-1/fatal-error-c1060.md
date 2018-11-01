---
title: Závažná chyba C1060
ms.date: 11/04/2016
f1_keywords:
- C1060
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
ms.openlocfilehash: 876ae7a368d2d1a1ee94a04fc9ecf50d0f4b8d78
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607062"
---
# <a name="fatal-error-c1060"></a>Závažná chyba C1060

kompilátoru je nedostatek místa v haldě

Operační systém nebo knihovny run-time nelze vyplnit žádost o paměti.

### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>Chcete-li vyřešit tuto chybu, zkuste následující možná řešení

1. Pokud kompilátor vyvolá také chyby [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) a [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md), použijte [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) – možnost kompilátoru snížit omezení přidělení paměti. Další místo v haldě je k dispozici pro vaši aplikaci, pokud můžete snížit zbývající přidělení paměti.

   Pokud [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) volba je již nastavena, zkuste ho odebrat. Vzhledem k tomu, že zadaný v možnosti limit přidělení paměti je příliš vysoká, může dojít k vyčerpání místo v haldě. Kompilátor používá výchozí omezení, pokud odeberete [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) možnost.

1. Při kompilaci na 64bitové platformě pomocí sady nástrojů kompilátoru 64-bit. Informace najdete v tématu [postupy: povolení 64bitová verze sady nástrojů Visual C++ v příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. Na Windows 32-bit, zkuste použít [3 GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) boot.ini přepínače.

1. Zvětšete velikost odkládacího souboru Windows.

1. Zavřete ostatní spuštěné programy.

1. Odstraňte nepotřebné vkládané soubory.

1. Odstraňte nepotřebné globální proměnné, například podle dynamickým přidělením paměti namísto deklarování velkého pole.

1. Odstraňte nepoužité deklarace.

9. Aktuální soubor rozdělte na menší soubory.