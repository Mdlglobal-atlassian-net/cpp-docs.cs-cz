---
title: Závažná chyba C1060
ms.date: 11/04/2016
f1_keywords:
- C1060
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
ms.openlocfilehash: f1a7c3ccab716a9281d4520f4c5fce2afff60187
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204435"
---
# <a name="fatal-error-c1060"></a>Závažná chyba C1060

Kompilátor má nedostatek prostoru v haldě.

Operační systém nebo knihovna run-time nemůže vyplnit požadavek na paměť.

### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>Pokud chcete tuto chybu opravit, vyzkoušejte následující možná řešení.

1. Pokud kompilátor také vydá chyby [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) a [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md), snižte limit přidělování paměti pomocí možnosti kompilátoru [/zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) . Další prostor haldy je k dispozici pro vaši aplikaci, pokud snížíte zbývající přidělení paměti.

   Pokud je už možnost [/zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) nastavená, zkuste ji odebrat. Je možné, že se vyčerpá prostor haldy, protože limit přidělení paměti zadaný v možnosti je příliš vysoký. Pokud odeberete možnost [/zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) , kompilátor použije výchozí limit.

1. Pokud kompilujete na 64 platformě, použijte sadu nástrojů kompilátoru 64. Informace naleznete v tématu [How to: Enable a 64-bit Visual C++ sada nástrojů na příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. V 32 Windows zkuste použít přepínač [/3gb](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) Boot. ini.

1. Zvětšete velikost souboru Windows swap-File.

1. Ukončete ostatní spuštěné programy.

1. Odstraňte nepotřebné vkládané soubory.

1. Eliminujte nepotřebné globální proměnné, například tím, že dynamicky přidělujete paměť místo deklarace velkého pole.

1. Odstraňte nepoužité deklarace.

9. Aktuální soubor rozdělte na menší soubory.
