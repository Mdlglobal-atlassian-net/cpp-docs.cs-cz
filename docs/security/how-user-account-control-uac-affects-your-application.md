---
title: Jak ovlivňuje nástroj Řízení uživatelských účtů (UAC) vaši aplikaci
ms.date: 11/19/2018
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
ms.openlocfilehash: 3702462ec892025cfb4f24d9c91e6db705b1b9a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179244"
---
# <a name="how-user-account-control-uac-affects-your-application"></a>Jak ovlivňuje nástroj Řízení uživatelských účtů (UAC) vaši aplikaci

Řízení uživatelských účtů (UAC) je funkce systému Windows Vista, ve které uživatelské účty mají omezená oprávnění. Můžete najít podrobné informace o nástroji Řízení uživatelských účtů na těchto místech:

- [Doporučené postupy pro vývojáře a pokyny pro aplikace v prostředí s nejnižšími oprávněními](/windows/desktop/uxguide/winenv-uac)

## <a name="building-projects-after-enabling-uac"></a>Vytváření projektů po povolení nástroje Řízení uživatelských účtů

Pokud vytváříte projekt jazyka Visual C++ v systému Windows Vista s nástroji Řízení uživatelských účtů, které jsou zakázané a později povolit nástroj Řízení uživatelských účtů, musí vyčistit a znovu sestavte projekt, aby mohly fungovat správně.

## <a name="applications-that-require-administrative-privileges"></a>Aplikace, které vyžadují oprávnění správce

Ve výchozím nastavení, vloží linker Visual C++ fragment nástroje Řízení uživatelských účtů do manifestu aplikace s úrovní provádění `asInvoker`. Pokud vaše aplikace vyžaduje oprávnění správce pro správnou funkci (například v případě, že upraví HKLM uzlu registru nebo pokud se zapíše do chráněných oblastech disku, jako je například adresář Windows), je třeba upravit vaší aplikace.

Prvním způsobem je upravit fragment nástroje Řízení uživatelských účtů v manifestu pro změnu úrovně spuštění na *requireAdministrator*. Aplikace pak vyzve uživatele pro přihlašovací údaje pro správu před jejím spuštěním. Informace o tom, jak to provést, najdete v tématu [/MANIFESTUAC (vložené informace UAC v manifestu)](../build/reference/manifestuac-embeds-uac-information-in-manifest.md).

Druhou možností je nevkládat fragment nástroje Řízení uživatelských účtů do manifestu tak, že zadáte `/MANIFESTUAC:NO` – možnost linkeru. Vaše aplikace poběží v tomto případě virtualizované. Všechny změny, které provedete v registru nebo systému souborů nebude zachována po ukončení vaší aplikace.

Následující diagram popisuje, jak vaše aplikace poběží v závislosti na tom, zda je povoleno nástroje Řízení uživatelských účtů a určuje, zda má aplikace manifestu nástroje Řízení uživatelských účtů:

![Chování Windows zavaděče](media/uacflowchart.png "chování Windows zavaděče")

## <a name="see-also"></a>Viz také:

[Osvědčené postupy zabezpečení](security-best-practices-for-cpp.md)
