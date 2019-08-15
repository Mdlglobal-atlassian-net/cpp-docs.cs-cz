---
title: Jak ovlivňuje nástroj Řízení uživatelských účtů (UAC) vaši aplikaci
ms.date: 11/19/2018
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
ms.openlocfilehash: 8c283e86a71092bb510892b6361f3d0fddc2abb6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510139"
---
# <a name="how-user-account-control-uac-affects-your-application"></a>Jak ovlivňuje nástroj Řízení uživatelských účtů (UAC) vaši aplikaci

Řízení uživatelských účtů (UAC) je funkce systému Windows Vista, ve které mají uživatelské účty omezená oprávnění. Podrobné informace o nástroji Řízení uživatelských účtů najdete v těchto lokalitách:

- [Osvědčené postupy a pokyny pro vývojáře pro aplikace s nejnižším privilegovaným prostředím](/windows/win32/uxguide/winenv-uac)

## <a name="building-projects-after-enabling-uac"></a>Vytváření projektů po povolení nástroje řízení uživatelských účtů

Pokud vytvoříte projekt sady Visual Studio C++ v systému Windows Vista s nástrojem Řízení uživatelských účtů zakázán a později povolíte nástroj řízení uživatelských účtů, je nutné projekt vyčistit a znovu sestavit, aby správně fungoval.

## <a name="applications-that-require-administrative-privileges"></a>Aplikace, které vyžadují oprávnění správce

Ve výchozím nastavení Visual C++ linker vloží fragment řízení uživatelských účtů do manifestu aplikace s úrovní `asInvoker`spuštění. Pokud vaše aplikace vyžaduje oprávnění správce ke správnému spuštění (například pokud změní uzel HKLM registru nebo pokud zapisuje do chráněných oblastí disku, jako je například adresář Windows), musíte aplikaci upravit.

První možností je změnit fragment nástroje řízení uživatelských účtů manifestu, aby se změnila úroveň spuštění na *vyžadovat správce*. Aplikace pak uživatele vyzve k zadání přihlašovacích údajů správce před jeho spuštěním. Další informace o tom, jak to provést, naleznete [v tématu/MANIFESTUAC (vložení informací o nástroji Řízení uživatelských účtů v manifestu)](../build/reference/manifestuac-embeds-uac-information-in-manifest.md).

Druhou možností je nevkládat do manifestu fragment řízení uživatelských účtů zadáním `/MANIFESTUAC:NO` Možnosti linkeru. V takovém případě se aplikace spustí virtualizované. Všechny změny, které provedete v registru nebo v systému souborů, nebudou po ukončení vaší aplikace zachovány.

Následující vývojový diagram popisuje, jak se vaše aplikace spustí v závislosti na tom, jestli je povolený nástroj řízení uživatelských účtů a jestli má aplikace manifest nástroje řízení uživatelských účtů:

![Chování zavaděče Windows](media/uacflowchart.png "Chování zavaděče Windows")

## <a name="see-also"></a>Viz také:

[Osvědčené postupy zabezpečení](security-best-practices-for-cpp.md)
