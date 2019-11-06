---
title: Portování knihoven třetích stran
ms.date: 10/29/2019
helpviewer_keywords:
- 3rd-party libraries
- vspkg
ms.assetid: b055ed20-8a9e-45b2-ac2a-e3d94271c009
ms.openlocfilehash: 89460af1ad0b356f4f5952141636a9f067131750
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627194"
---
# <a name="porting-third-party-libraries"></a>Portování knihoven třetích stran

Při upgradu projektu z Visual Studio 2013 nebo předchozí na aktuální verzi vizuálu C++je také nutné upgradovat všechny knihovny, které projekt používá, aby knihovna a projekt byly sestaveny se stejnou verzí a charakterem kompilátoru. Pokud nemáte přístup ke zdrojovému kódu knihovny a knihovna není k dispozici prostřednictvím vcpkg, musíte získat aktualizovaný binární soubor od dodavatele knihovny. (Další informace najdete v tématu [Přehled potenciálních problémů s upgradem](overview-of-potential-upgrade-issues-visual-cpp.md)).

Při upgradu aplikace ze sady Visual Studio 2015 nebo Visual Studio 2017 na Visual Studio 2019 není nutné upgradovat závislosti, protože kód vygenerovaný těmito třemi verzemi je binární kompatibilní. Další informace naleznete v tématu [ C++ binární kompatibilita mezi Visual Studio 2015 a Visual Studio 2019](binary-compat-2015-2017.md).

## <a name="vcpkg-for-open-source-libraries"></a>vcpkg pro open source knihovny

V minulosti bylo hledání a upgrade knihoven třetích stran někdy netriviální úloha. Aby bylo snazší získat a znovu sestavovat C++ open source knihovny třetích stran, vytvořil vizuální C++ tým nástroj příkazového řádku, který se nazývá nástroj pro **balení VC + +** nebo **vcpkg**. Vcpkg má katalog s možností vyhledávání mnoha oblíbených C++ Open Source knihoven. Libovolnou knihovnu v katalogu můžete nainstalovat přímo z příkazového řádku vcpkg. Při instalaci knihovny vytvoří Vcpkg ve vašem počítači stromovou strukturu a do této složky přidá. h,. lib a binární soubory. Tuto složku můžete použít v příkazovém řádku kompilace nebo ji integrovat do sady Visual Studio 2015 nebo novější pomocí příkazu integrace vcpkg Integration Install. Po integraci umístění knihovny může Visual Studio najít ho a přidat ho do libovolného nového projektu, který vytvoříte. Chcete-li použít knihovnu, stačí ji `#include` a Visual Studio automaticky přidá cestu. lib k nastavení projektu a zkopíruje knihovnu DLL do složky řešení. Další informace najdete v tématu [vcpkg: Správce balíčků pro C++ ](../build/vcpkg.md).

## <a name="reporting-issues"></a>Vytváření sestav – problémy

Pokud vaše open source knihovna není přítomna v katalogu **vcpkg** , můžete otevřít problém v [úložišti GitHub](https://github.com/Microsoft/vcpkg/issues) , kde ho komunita a Visual C++ tým uvidí a případně můžou vytvořit soubor portu pro tuto knihovnu.

## <a name="see-also"></a>Viz také:

[Průvodce přenosem a upgradem Visual C++](visual-cpp-porting-and-upgrading-guide.md)
