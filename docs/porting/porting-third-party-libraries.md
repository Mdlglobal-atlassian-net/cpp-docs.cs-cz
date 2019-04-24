---
title: Přenos knihoven třetích stran
ms.date: 01/10/2017
helpviewer_keywords:
- 3rd-party libraries
- vspkg
ms.assetid: b055ed20-8a9e-45b2-ac2a-e3d94271c009
ms.openlocfilehash: e1aefc82eb23a8479035dd3372fa9ec24ab8feb1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337229"
---
# <a name="porting-third-party-libraries"></a>Přenos knihoven třetích stran

Při upgradu projektu na aktuální verzi jazyka Visual C++, musíte také upgradovat všechny knihovny, které používá projekt tak, aby knihovny a váš projekt jsou vybaveny stejnou verzi a flavor kompilátoru. (Další informace najdete v tématu [přehled potenciálních problémů s upgradem](overview-of-potential-upgrade-issues-visual-cpp.md)).

## <a name="introducing-vcpkg"></a>Představujeme vcpkg

V minulosti byl někdy netriviální úkolů hledání a upgrade knihovny 3. stran. Do usnadňují získání a znovu sestavte C++ 3. stran open source knihoven Visual C++ tým vytvořil nástroj příkazového řádku, volá se, **balení nástrojů VC ++** nebo **vcpkg**. Vcpkg má katalog mnoho oblíbených open source knihoven C++. V katalogu přímo z příkazového řádku vcpkg můžete nainstalovat všechny knihovny. Při instalaci knihovny Vcpkg vytvoří stromu adresáře na počítači a přidá .h, .lib a binární soubory v této složce. Můžete použít tuto složku v příkazovém řádku kompilace, nebo ji integrovat do sady Visual Studio 2015 nebo později pomocí vcpkg integrace instalačního příkazu. Po integraci umístění knihovny sady Visual Studio můžete najít ho a přidat ho do nového projektu, který vytvoříte. Pro použití knihovny, právě `#include` a sady Visual Studio bude automaticky přidat cestu .lib do nastavení projektu a kopírování knihovny dll do složky řešení. Další informace najdete v tématu [vcpkg: Správce balíčků pro C++](../build/vcpkg.md).

## <a name="reporting-issues"></a>Hlášení problémů s

Pokud není k dispozici v knihovně **vcpkg** katalogu, které otevřete problém na [úložiště GitHub se vzorovými](https://github.com/Microsoft/vcpkg/issues) kde komunity a týmu Visual C++ můžete podívat, jak to a potenciálně vytvořit soubor port pro tuto knihovnu.

Pro nechráněný 3 stran knihovny (není otevřený zdroj) doporučujeme, abyste se obrátili zprostředkovatele knihovny. Ale jsme chtěli vědět o žádné speciální knihovny používají a zablokuje, dejte nám vědět, které z nich záviset na (můžete kontaktujte nás na adrese vcupgrade@microsoft.com).

## <a name="see-also"></a>Viz také:

[Průvodce přenosem a upgradem Visual C++](visual-cpp-porting-and-upgrading-guide.md)
