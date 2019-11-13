---
title: C++binární kompatibilita mezi Visual Studio 2015, 2017 a 2019
description: Popisuje způsob fungování binární kompatibility mezi kompilovanými C++ soubory v sadě Visual Studio 2015, 2017 a 2019. Jeden balíček Microsoft C++ Visual Redistributable Package funguje pro všechny tři verze.
ms.date: 11/11/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: 118ad0a32d5dc8c344967f9a67f2d5b05aa806c0
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965557"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-2017-and-2019"></a>C++binární kompatibilita mezi Visual Studio 2015, 2017 a 2019

Sady nástrojů C++ kompilátoru Microsoft (MSVC) v Visual Studio 2013 a dříve nezaručují binární kompatibilitu mezi verzemi. Nemůžete propojit soubory objektů, statické knihovny, dynamické knihovny a spustitelné soubory sestavené různými verzemi. Instrukce ABI, formáty objektů a běhové knihovny jsou nekompatibilní.

Toto chování jsme změnili v aplikaci Visual Studio 2015, 2017 a 2019. Běhové knihovny a aplikace zkompilované některou z těchto verzí kompilátoru jsou binární kompatibilní. Odráží se v hlavním čísle sady C++ nástrojů, což je 14 pro všechny tři verze. (Verze sady nástrojů je v140 pro Visual Studio 2015, v141 pro 2017 a V142 pro 2019). Řekněme, že máte knihovny třetích stran sestavené pomocí sady Visual Studio 2015. Můžete je nadále používat v aplikaci vytvořené pomocí sady Visual Studio 2017 nebo 2019. Není nutné znovu kompilovat s vyhovující sadou nástrojů. Nejnovější verze balíčku Microsoft Visual C++ Redistributable Package (Redistributable) funguje pro všechny.

Toto pravidlo obsahuje výjimku: statické knihovny nebo soubory objektů zkompilované pomocí přepínače `/GL` kompilátoru *nejsou* binární kompatibilní napříč verzemi.

Redistribuovatelná verze vaší aplikace má důležité omezení binární kompatibility. Platí při kombinaci binárních souborů sestavených s různými podporovanými verzemi sady nástrojů. Distribuovatelný verze musí být alespoň stejná jako poslední sada nástrojů, kterou používá kterákoli součást aplikace.

## <a name="upgrade-the-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>Upgrade Microsoft Visual C++ Redistributable ze sady visual Studio 2015 nebo 2017 na visual Studio 2019

Pro Visual Studio 2015, 2017 C++ a 2019 jsme si ponechali číslo hlavní verze Microsoft Visual Redistributable. To znamená, že je možné nainstalovat jenom jednu instanci redistribuovatelného programu. Novější verze přepíše všechny starší verze, které jsou již nainstalovány. Například jedna aplikace může nainstalovat Distribuovatelný balíček ze sady Visual Studio 2015. Pak jiná aplikace nainstaluje redistribuovatelný balíček ze sady Visual Studio 2019. Verze 2019 Přepisuje starší verzi, ale vzhledem k tomu, že se jedná o binární kompatibilitu, starší aplikace pořád funguje správně. Ujistěte se, že nejnovější verze distribuovatelných funkcí obsahuje všechny nejnovější funkce, aktualizace zabezpečení a opravy chyb. To je důvod, proč vždycky doporučujeme upgradovat na nejnovější dostupnou verzi.

Podobně nemůžete nainstalovat starší Distribuovatelný balíček, pokud už je nainstalovaná novější verze. Pokud se pokusíte, instalační program ohlásí chybu. Pokud nainstalujete 2015 nebo 2017 Distribuovatelný na počítač, který už má verzi 2019, zobrazí se chyba.

```Output
0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.
```

Tato chyba je záměrné. Doporučujeme zachovat nainstalovanou nejnovější verzi. Ujistěte se, že instalační program může z této chyby v tichém režimu obnovit.

## <a name="see-also"></a>Viz také:

[\ C++ historie změn vizuálů](../porting/visual-cpp-change-history-2003-2015.md)
[Nejnovější podporované vizuální C++ redistribuovatelné soubory ke stažení](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)
