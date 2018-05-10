---
title: Spuštění jako člen skupiny Users | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- PRJ0050
- VCD0047
dev_langs:
- C++
helpviewer_keywords:
- Users Group [C++]
- security [C++], Users Group
- Windows accounts [C++]
- non administrator users [C++]
- user accounts [C++]
- administrator (not running as) [C++]
ms.assetid: e48a03ec-d345-49f6-809a-1a291eecbc81
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4faeae9100cf6e60a2eeda19baea20ba42be197f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="running-as-a-member-of-the-users-group"></a>Spuštění jako člen skupiny Users
Toto téma vysvětluje, jak konfigurace uživatelské účty systému Windows jako člen skupiny Users (na rozdíl od skupiny Administrators) zvyšuje úroveň zabezpečení snižuje pravděpodobnost infekce škodlivým kódem.  
  
## <a name="security-risks"></a>Rizika zabezpečení  
 Jako správce je zranitelný systému několik druhů útokům na zabezpečení, jako je například "Trojský kůň" a "přetečení vyrovnávací paměti." Pouze navštívení web na Internetu jako správce může poškodit systému, jako škodlivý kód, který byl stažen z web na Internetu může zaútočit na váš počítač. Pokud bylo úspěšné, dědí oprávnění správce a potom může provést akce, například odstraní všechny soubory, přeformátování vašeho pevného disku a vytvoření nového uživatele účty s přístupem pro správu.  
  
## <a name="non-administrator-user-groups"></a>Skupiny uživatelů bez oprávnění správce  
 Uživatelské účty systému Windows, které obvykle používají vývojáři musí být přidaní do uživatelé nebo skupiny Power Users. Vývojáři musí být také přidaní do skupiny ladění. Členství ve skupině uživatelů umožňuje provádět běžné úlohy, včetně spouštění programů a hostujících internetovými weby bez vystavení vašeho počítače zbytečnému riziku. Jako člena skupiny Power Users můžete také provést úlohy, jako je instalace aplikace, instalace tiskárny a většinu operací ovládací panely. Pokud potřebujete k provádění úloh správy, jako je například upgrade operačního systému nebo konfigurace systémových parametrů, je zapotřebí přihlásit k účtu správce na tak dlouho potřeba provádět správu úloh. Alternativně Windows **runas** příkaz lze použít ke spuštění určitých aplikací s přístupem pro správu.  
  
## <a name="exposing-customers-to-security-risks"></a>Vystavení zákazníkům rizika zabezpečení  
 Nebude součástí skupiny Administrators je zvláště důležité pro vývojáře, protože, kromě ochrany počítače vývoj, brání vývojáři nechtěně psaní kódu, který vyžaduje zákazníků k zapojení do skupiny Administrators pořadí spuštění aplikace, že budete vyvíjet. Pokud kód, který vyžaduje přístup správce byla zavedená během vývoje, se nezdaří za běhu, výstrahy upozorňující na skutečnost, že teď vaše aplikace vyžaduje zákazníkům spustit jako správce.  
  
## <a name="code-that-requires-administrator-privileges"></a>Kód, který vyžaduje oprávnění správce  
 Kód spuštění vyžaduje přístup správce. Pokud je to možné mají být naplněny alternativy tento kód. Příklady kódu činnosti, které vyžadují přístup správce:  
  
-   Zápis do chráněných oblastech systému souborů, jako je například adresáře systému Windows nebo Program Files  
  
-   Zápis do chráněných oblastech registru, jako je například HKEY_LOCAL_MACHINE  
  
-   Instalace sestavení v globální mezipaměti sestavení (GAC)  
  
 Obecně platí tyto akce musí být omezeno na instalační programy aplikace. To umožňuje uživatelům používat pouze dočasně správce stavu.  
  
## <a name="debugging"></a>Ladění  
 Můžete ladit aplikace, které spustíte v sadě Visual Studio (nativní a nespravované) jako bez oprávnění správce ve stane součástí skupiny ladění. To zahrnuje možnost připojení k spuštěné aplikaci pomocí připojení k procesu příkazu. Nicméně je nutné být součástí skupiny správce, pokud chcete ladit nativní nebo spravované aplikace, které nebyly spuštěny jiným uživatelem.  
  
## <a name="see-also"></a>Viz také  
 [Osvědčené postupy zabezpečení](security-best-practices-for-cpp.md)