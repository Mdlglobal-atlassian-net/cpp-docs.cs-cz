---
title: Průvodce zprostředkovatele OLE DB ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.provider.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL OLE DB Provider Wizard
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 827b46de299341f23d0b799a5ed44b8923bbc182
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357477"
---
# <a name="atl-ole-db-provider-wizard"></a>Průvodce zprostředkovatele OLE DB knihovny ATL
Tento průvodce vytvoří třídy, které tvoří zprostředkovatele OLE DB.  
  
## <a name="remarks"></a>Poznámky  
 Počínaje verzí Visual Studio 2008, registrace skript vytvořený tímto průvodcem bude registrovat jeho komponenty COM v **HKEY_CURRENT_USER** místo **HKEY_LOCAL_MACHINE**. Chcete-li toto chování změnit, nastavte **zaregistrovat součást pro všechny uživatele** možnost ATL průvodce.  
  
 Následující tabulka popisuje možnosti Průvodce zprostředkovatele OLE DB ATL:  
  
 **Krátký název**  
 Zadejte krátký název zprostředkovatele, který má být vytvořen. Upravit pole v Průvodci se automaticky vyplní podle co zadáte zde. Pokud chcete, můžete upravit další pole názvů.  
  
 **Třída typu coclass**  
 Název coclass. Název identifikátoru ProgID se změní na shodovat s tímto názvem.  
  
 **S atributy**  
 Tato možnost určuje, zda má průvodce vytvořit pomocí atributů nebo deklarací šablon třídy zprostředkovatele. Když vyberete tuto možnost, používá průvodce atributy namísto deklarace šablon (Toto je výchozí možnost, pokud jste vytvořili projekt s atributy). Když zrušíte zaškrtnutí tohoto políčka, používá průvodce deklarace šablon namísto atributů (Toto je výchozí možnost, pokud jste vytvořili projekt s atributy).  
  
 Pokud vyberete tuto možnost, při vytváření projektu bez s atributy, Průvodce vás upozorní, že projekt bude převeden do projektu s atributy a zobrazí dotaz, zda chcete-li pokračovat, nebo ne.  
  
 **ProgID**  
 ProgID nebo programový identifikátor je textový řetězec, který vaše aplikace může použít místo identifikátor GUID. ProgID Název má formulář *Projectname.Coclassname*.  
  
 **Verze**  
 Číslo verze poskytovatele. Výchozí hodnota je 1.  
  
 **Třída zdroje dat**  
 Název třídy zdroje dat formuláře C*Shortname*zdroje.  
  
 **Zdroj dat souboru h**  
 Soubor hlaviček pro datové třídy zdroje. Můžete upravit název tohoto souboru nebo vyberte existující soubor hlavičky.  
  
 **Relace – třída**  
 Název třídy relace formuláře C*Shortname*relace.  
  
 **Soubor h relace**  
 Soubor hlaviček pro třídu relace. Můžete upravit název tohoto souboru nebo vyberte existující soubor hlavičky.  
  
 **Příkaz – třída**  
 Název třídy příkazu formuláře C*Shortname*příkaz.  
  
 **Příkaz .h soubor**  
 Soubor hlaviček pro třídu příkazu. Tento název nelze upravit a závisí na název souboru záhlaví řádků.  
  
 **Třídy sady řádků**  
 Název třídy sady řádků formuláře C*Shortname*sady řádků.  
  
 **Soubor h sady řádků**  
 Soubor hlaviček pro třídu sady řádků. Můžete upravit název tohoto souboru nebo vyberte existující soubor hlavičky.  
  
 **Sada řádků souboru**  
 Soubor implementace poskytovatele. Můžete upravit název tohoto souboru nebo vyberte existující soubor implementace.  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatel OLE DB knihovny ATL](../../atl/reference/adding-an-atl-ole-db-provider.md)

