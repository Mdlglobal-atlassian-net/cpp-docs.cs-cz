---
title: Spuštění jako člen skupiny Users
ms.date: 11/04/2016
helpviewer_keywords:
- Users Group [C++]
- security [C++], Users Group
- Windows accounts [C++]
- non administrator users [C++]
- user accounts [C++]
- administrator (not running as) [C++]
ms.assetid: e48a03ec-d345-49f6-809a-1a291eecbc81
ms.openlocfilehash: 117ef426950fc9aff5ae41e894f0d7ae898369cd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445440"
---
# <a name="running-as-a-member-of-the-users-group"></a>Spuštění jako člen skupiny Users

Toto téma vysvětluje, jak konfigurovat uživatelské účty systému Windows jako člena skupiny uživatelů (na rozdíl od skupiny správců) zvyšuje zabezpečení tím, že snižuje pravděpodobnost napadení škodlivým kódem.

## <a name="security-risks"></a>Bezpečnostní rizika

Spuštění jako správce způsobí, že váš systém bude zranitelný vůči několika druhům útokům na zabezpečení, jako je například trojský kůň a přetečení vyrovnávací paměti. Jenom navštěvování internetového webu jako správce může poškodit systém, protože škodlivý kód, který se stahuje z webu na internetu, může ohrozit váš počítač. V případě úspěchu zdědí vaše oprávnění správce a může provádět akce, jako je odstranění všech souborů, přeformátování pevného disku a vytvoření nových uživatelských účtů s přístupem správce.

## <a name="non-administrator-user-groups"></a>Skupiny uživatelů bez oprávnění správce

Uživatelské účty systému Windows, které vývojáři používají normálně, by se měly přidat do skupin uživatelé nebo skupiny Power Users. Do skupiny pro ladění byste měli také přidat vývojáře. Když je členem skupiny uživatelů, můžete provádět běžné úlohy, včetně spouštění programů a navštěvování internetových webů, aniž byste počítač vystavili na zbytečné riziko. Jako člen skupiny Power Users můžete také provádět úlohy, jako je například instalace aplikace, instalace tiskárny a většina operací ovládacích panelů. Pokud potřebujete provádět úlohy správy, jako je například upgrade operačního systému nebo konfigurace systémových parametrů, měli byste se přihlásit k účtu správce, který vám stačí dostatečně dlouho provést úlohu správy. Alternativně lze příkaz Windows **runas** použít ke spuštění konkrétních aplikací s přístupem správce.

## <a name="exposing-customers-to-security-risks"></a>Vystavení zákazníků bezpečnostním rizikům

Mimo skupinu správců je zvláště důležité pro vývojáře, protože kromě ochrany vývojových počítačů brání vývojářům v neúmyslném psaní kódu, který vyžaduje, aby se zákazníci připojili ke skupině Administrators v. aby bylo možné spouštět aplikace, které vyvíjíte. Pokud je kód, který vyžaduje přístup správce, zavedený během vývoje, selže za běhu a upozorní vás na skutečnost, že vaše aplikace teď vyžaduje, aby se zákazníci spouštěli jako správci.

## <a name="code-that-requires-administrator-privileges"></a>Kód, který vyžaduje oprávnění správce

Určitý kód vyžaduje přístup správce, aby bylo možné provést. Pokud je to možné, měly by se použít alternativy k tomuto kódu. Příklady operací s kódem, které vyžadují přístup správce:

- Zápis do chráněných oblastí systému souborů, jako jsou například adresáře Windows nebo soubory programu

- Zápis do chráněných oblastí registru, například HKEY_LOCAL_MACHINE

- Instalace sestavení do globální mezipaměti sestavení (GAC)

Obecně platí, že tyto akce by měly být omezeny na instalační programy aplikací. To umožňuje uživatelům používat stav správce jenom dočasně.

## <a name="debugging"></a>Ladění

Můžete ladit jakékoli aplikace, které spustíte v rámci sady Visual Studio (nativní a nespravované) jako nesprávce, protože se stanou součástí skupiny ladění. To zahrnuje možnost připojit se ke spuštěné aplikaci pomocí příkazu připojit k procesu. Je však nutné být součástí skupiny správců, aby bylo možné ladit nativní nebo spravované aplikace, které byly spuštěny jiným uživatelem.

## <a name="see-also"></a>Viz také

[Osvědčené postupy zabezpečení](security-best-practices-for-cpp.md)
