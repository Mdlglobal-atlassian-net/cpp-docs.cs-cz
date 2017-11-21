---
title: "-GUARD (povolení kontroly ochrany) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dbc987f7db1e3a1bce0b73f0c21e875b7c9e5eda
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="guard-enable-guard-checks"></a>/GUARD (povolení kontroly ochrany)
Určuje podporu pro ochranu toku řízení kontroly v spustitelné bitové kopie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GUARD:{CF|NO}  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud je zadána /GUARD:CF, upraví linkeru záhlaví .dll nebo .exe označíte, podporu pro řízení toku Guard (CFG) runtime kontroly. Požadovaný ovládací prvek toku cílová adresa data linkeru také přidá do hlavičky. Ve výchozím nastavení je /GUARD:CF zakázaná. Lze ji explicitně vypnout pomocí /GUARD:NO. Platnost /GUARD:CF taky vyžaduje [/DYNAMICBASE (použijte adresu místa rozložení náhodné)](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) – možnost linkeru, který je ve výchozím.  
  
 Když kompilace zdrojového kódu pomocí [/guard:cf](../../build/reference/guard-enable-control-flow-guard.md) možnost kompilátor analyzuje tok řízení tak, že prověří všechny nepřímé volání pro adresy možný cíl. Kompilátor vloží kódu k ověření, že cílová adresa instrukce nepřímé volání je v seznamu známých cílové adresy za běhu. Zkontrolujte operační systémy, které podporují CFG stop programu, který selže CFG runtime. Díky tomu je pro útočníka ke spuštění škodlivého kódu s použitím poškození dat. Chcete-li změnit cíl volání obtížnější.  
  
 Je třeba zadat možnost /GUARD:CF kompilátoru a linkeru pro vytvoření povoleno CFG spustitelné bitové kopie. Kód kompilovat, ale nejsou spojeny pomocí /GUARD:CF vznikly náklady kontrol za běhu, ale neumožňuje CFG ochrany. Když je možnost /GUARD:CF nastavené `cl` příkaz pro zkompilování a spojení v jednom kroku, kompilátor předá příznak linkeru. Když **řízení toku ochrana** je nastavena v sadě Visual Studio, možnost /GUARD:CF předaný kompilátoru a linkeru. Pokud soubory objektů nebo knihovny sestavili jsme samostatně, možnost musí být explicitně zadaná v `link` příkaz.  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte položku **vlastnosti konfigurace**, **Linkeru**, **příkazového řádku**.  
  
3.  V **další možnosti**, zadejte `/GUARD:CF`.  
  
## <a name="see-also"></a>Viz také  
 [/ Guard (povolení ochrany toku řízení)](../../build/reference/guard-enable-control-flow-guard.md)   
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)