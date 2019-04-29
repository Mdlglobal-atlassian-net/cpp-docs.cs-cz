---
title: Spuštění jako člen skupiny Users
ms.date: 11/04/2016
f1_keywords:
- PRJ0050
- VCD0047
helpviewer_keywords:
- Users Group [C++]
- security [C++], Users Group
- Windows accounts [C++]
- non administrator users [C++]
- user accounts [C++]
- administrator (not running as) [C++]
ms.assetid: e48a03ec-d345-49f6-809a-1a291eecbc81
ms.openlocfilehash: dc06e2dc58d28c34a646ccffc0be90368b3297f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411289"
---
# <a name="running-as-a-member-of-the-users-group"></a>Spuštění jako člen skupiny Users

Toto téma vysvětluje, jak konfigurace Windows uživatelské účty jako člen skupiny Users (na rozdíl od skupiny Administrators) zvyšuje úroveň zabezpečení omezuje se tak pravděpodobnost infekce škodlivým kódem.

## <a name="security-risks"></a>Bezpečnostní rizika

Přihlášení jako správce je zranitelný systému několik druhů útokům na zabezpečení, jako je například "Trojský kůň" a "přetečení vyrovnávací paměti." Pouze navštívení webem na Internetu jako správce můžete poškození systému, jako škodlivý kód, který se stáhne z webem na Internetu může napadení počítače. V případě úspěchu se dědí oprávnění správce a pak můžete provádět akce, například odstraní všechny soubory, přeformátování vašeho pevného disku a vytvoření nové uživatelské účty s přístupem pro správu.

## <a name="non-administrator-user-groups"></a>Skupiny uživatelů bez oprávnění správce

Uživatelské účty Windows, které obvykle používají vývojáři měli byste přidat uživatele nebo skupiny Power Users. Vývojáři by také přidat do skupiny ladění. Člen skupiny Users umožňuje provádět běžné úlohy, včetně spouštění programů a hostujících internetovými weby bez vystavení počítače zbytečné riziko. Jako člen skupiny Power Users můžete také provádět úkoly jako instalace aplikací, instalace tiskárny a většina operací Ovládacích panelů. Pokud potřebujete k provádění úloh správy, jako je upgrade operačního systému nebo konfigurace parametrů systému, by měl přihlásíte s oprávněními správce na tak dlouho dostačující k provedení úloh pro správu. Alternativně Windows **runas** příkaz můžete použít ke spuštění konkrétní aplikací s přístupem pro správu.

## <a name="exposing-customers-to-security-risks"></a>Zákazníci na bezpečnostní rizika vystavení

Není součástí skupiny Administrators je obzvláště důležité pro vývojáře, protože kromě ochrany počítačích vývojářů, brání vývojářům od nedopatřením psaní kódu, který vyžaduje, aby zákazníci připojit do skupiny Administrators pořadí aplikace spustí, že při vývoji. Pokud kód, který vyžaduje přístup správce se používá při vývoji, dojde k selhání za běhu, upozorní vás na to, že teď vaše aplikace vyžaduje, aby zákazníci spustit jako správce.

## <a name="code-that-requires-administrator-privileges"></a>Kód, který vyžaduje oprávnění správce

Nějaký kód vyžaduje přístup správce k provedení. Pokud je to možné by měl být sledované alternativy na tento kód. Příklady kódu operace, které vyžadují přístup správce:

- Zápis do chráněné oblasti systému souborů, jako je například Windows nebo Program Files adresáře

- Zápis do registru, jako je například HKEY_LOCAL_MACHINE chráněné oblasti

- Instalace sestavení v globální mezipaměti sestavení (GAC)

Obecně tyto akce by měly být omezené na instalační programy aplikací. To umožňuje uživatelům používat Správce stavu jenom dočasně.

## <a name="debugging"></a>Ladění

Můžete ladit všechny aplikace, které spustíte v sadě Visual Studio (nativní a nespravovaných) jako bez oprávnění správce, že se stanete součástí skupiny ladění. To zahrnuje možnost se připojit k běžící aplikaci příkazu připojit k procesu. Nicméně je nutné být členem skupiny Administrator, aby bylo možné ladit spravované nebo nativní aplikace, které byly spouštěny jiným uživatelem.

## <a name="see-also"></a>Viz také:

[Osvědčené postupy zabezpečení](security-best-practices-for-cpp.md)
