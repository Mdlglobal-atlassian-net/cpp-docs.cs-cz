---
title: "Chyba linkerů Lnk1168 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1168
dev_langs:
- C++
helpviewer_keywords:
- LNK1168
ms.assetid: 97ead151-fd99-46fe-9a1d-7e84dc0b8cc8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 12dfce4243f0872735158df7ccd81b7c6e29efc8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1168"></a>Chyba linkerů LNK1168
Soubor nelze otevřít pro zápis  
  
 Nelze zapisovat linkeru `filename`. Je možné, že se soubor používá a jeho popisovač je uzamčen jiným procesem, nebo že nemáte oprávnění k zápisu do souboru nebo adresáře či síťové sdílené složky, ve které se nachází. Tato chyba je způsobená často přechodného stavu – například zámek držené antivirový program, soubor vyhledávání indexování proces, nebo zpoždění při uvolňování zámku ukládaná společností [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] sestavení systému.  
  
 Chcete-li tento problém vyřešit, ověřte, zda `filename` popisovač souboru není uzamčen a zda máte oprávnění k zápisu pro soubor. Pokud se jedná o spustitelný soubor, ověřte, zda již není spuštěn.  
  
 Můžete použít také nástroje webu Windows SysInternals [zpracování](http://technet.microsoft.com/sysinternals/bb896655.aspx) nebo [Průzkumníka procesů](http://technet.microsoft.com/sysinternals/bb896653) určit, které proces má soubor zpracování zámku na `filename`. Process Explorer můžete použít také k uvolnění zámků u otevřených popisovačů souborů. Informace o použití těchto nástrojů naleznete v souborech nápovědy, které se s nimi dodávají.  
  
 Pokud je soubor uzamčen antivirovým programem, můžete tento problém vyřešit tím, že výstupní adresáře sestavení vyloučíte z jeho kontroly. Kontroly antivirových programů se často spouštějí při vytvoření nových souborů v systému souborů, přičemž během kontroly jsou tyto soubory uzamčeny. Podrobné informace o tom, jak z kontroly vyloučit konkrétní adresáře, naleznete v dokumentaci k antivirovému programu.  
  
 Pokud je soubor uzamčen indexovací službou vyhledávání, můžete tento problém vyřešit tím, že výstupní adresáře sestavení vyloučíte z automatického indexování. Další informace naleznete v dokumentaci k indexovací službě. Chcete-li změnit indexování služby vyhledávání systému Windows, použijte **možnosti indexování** v systému Windows **ovládací panely**. Další informace najdete v tématu [vylepšit Windows vyhledávání pomocí indexu: Nejčastější dotazy](http://windows.microsoft.com/en-us/windows/improve-windows-searches-using-index-faq#1TC=windows-7).  
  
 Pokud proces sestavení nemůže přepsat spustitelný soubor, může být uzamčen Průzkumníkem souborů. Pokud **používání aplikací** služby byl zakázán, může Průzkumníka souborů přidržením zámek popisovač spustitelného souboru je delší dobu. Chcete-li tento problém vyřešit, spusťte **services.msc** a pak otevřete **vlastnosti** dialogové okno pro **používání aplikací** služby. Změna **typ spuštění** z **zakázané** k **ruční**.  
  
## <a name="see-also"></a>Viz také  
 [Můžete obdržet "Chyba PRJ0008" nebo "Kritické error LNK1168" chybová zpráva při pokusu o sestavení řešení nebo projektu ActiveX v jazyce Visual C++](http://support.microsoft.com/kb/308358)