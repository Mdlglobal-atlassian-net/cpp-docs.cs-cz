---
title: Chyba linkerů LNK1168
ms.date: 11/04/2016
f1_keywords:
- LNK1168
helpviewer_keywords:
- LNK1168
ms.assetid: 97ead151-fd99-46fe-9a1d-7e84dc0b8cc8
ms.openlocfilehash: d18aacd23a7ce9ed49f12a62f8358bb6d668c778
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622115"
---
# <a name="linker-tools-error-lnk1168"></a>Chyba linkerů LNK1168

Soubor nelze otevřít pro zápis

Linker nemůže zapisovat do `filename`. Je možné, že se soubor používá a jeho popisovač je uzamčen jiným procesem, nebo že nemáte oprávnění k zápisu do souboru nebo adresáře či síťové sdílené složky, ve které se nachází. Tato chyba je často způsobeno o dočasný stav – například zámek drží antivirového programu, indexovacím procesem vyhledávání souborů nebo prodlevou při uvolnění zámku drží systém sestavení Visual Studio.

Chcete-li vyřešit tento problém, ověřte, že `filename` není popisovač je uzamčen a zda máte oprávnění k zápisu souboru. Pokud se jedná o spustitelný soubor, ověřte, zda již není spuštěn.

Můžete použít také nástroje Windows SysInternals [zpracování](http://technet.microsoft.com/sysinternals/bb896655.aspx) nebo [Process Explorer](http://technet.microsoft.com/sysinternals/bb896653) k určení, který proces uzamkl popisovač souboru `filename`. Process Explorer můžete použít také k uvolnění zámků u otevřených popisovačů souborů. Informace o použití těchto nástrojů naleznete v souborech nápovědy, které se s nimi dodávají.

Pokud je soubor uzamčen antivirovým programem, můžete tento problém vyřešit tím, že výstupní adresáře sestavení vyloučíte z jeho kontroly. Kontroly antivirových programů se často spouštějí při vytvoření nových souborů v systému souborů, přičemž během kontroly jsou tyto soubory uzamčeny. Podrobné informace o tom, jak z kontroly vyloučit konkrétní adresáře, naleznete v dokumentaci k antivirovému programu.

Pokud je soubor uzamčen indexovací službou vyhledávání, můžete tento problém vyřešit tím, že výstupní adresáře sestavení vyloučíte z automatického indexování. Další informace naleznete v dokumentaci k indexovací službě. Ke změně indexovací služby vyhledávání Windows, použijte **možnosti indexování** v Windows **ovládací panely**. Další informace najdete v tématu [vylepšit Windows vyhledávání pomocí indexu: Nejčastější dotazy k](http://windows.microsoft.com/windows/improve-windows-searches-using-index-faq#1TC=windows-7).

Pokud proces sestavení nemůže přepsat spustitelný soubor, může být uzamčen Průzkumníkem souborů. Pokud **funkčnost aplikací** služba byla zakázána, Průzkumníka souborů může blokovat zámek popisovače spustitelného souboru po delší dobu. Chcete-li tento problém vyřešit, spusťte **services.msc** a pak otevřete **vlastnosti** dialogové okno pro **funkčnost aplikací** služby. Změnit **typ spouštění** z **zakázané** k **ruční**.
