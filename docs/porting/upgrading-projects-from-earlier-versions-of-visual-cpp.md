---
title: "Upgradování projektů z dřívějších verzí aplikace Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
caps.latest.revision: "36"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b141efa2ffa7d382278365101fca25b66ea25614
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="upgrading-projects-from-earlier-versions-of-visual-c"></a>Upgradování projektů z dřívějších verzí aplikace Visual C++
Ve většině případů můžete otevřít projekt, který byl vytvořen ve starší verzi sady Visual Studio. Je ale nutné projekt v sadě Visual Studio upgradovat. Pokud tento upgradovaný projekt uložíte, nelze ho už pak otevřít v předchozí verzi.  
  
> [!IMPORTANT]
>  Pokud se pokusíte převést projekt, který již byl převeden, zobrazí Visual Studio výzvu k potvrzení, protože zpětný převod odstraní existující soubory.  
  
 Mnoho upgradovaných projektů a řešení lze úspěšně sestavit bez jakýchkoli úprav. U některých projektů však mohou být nutné změny nastavení, zdrojového kódu nebo obojího. Při řešení potíží s nastavením doporučujeme nejprve postupovat podle následujících pokynů. Pokud se projekt stále nedaří sestavit, pokuste se vyřešit problémy v kódu. Další informace najdete v tématu [přehled potenciální problémy upgradu](../porting/overview-of-potential-upgrade-issues-visual-cpp.md).  
  
1.  Vytvořte kopii existujícího projektu a souborů řešení. Nainstalujte aktuální a starší verzi sady Visual Studio paralelně, abyste mohli v případě potřeby porovnávat verze souborů.  
  
2.  Otevřete kopii projektu nebo řešení v aktuální verzi sady Visual Studio, tím je upgradujte a poté uložte.  
  
3.  Pro každý převedeného projektu, otevřete místní nabídku a vyberte **vlastnosti**. V části **vlastnosti konfigurace**, vyberte **Obecné** a pak pro **sada nástrojů platformy**, vyberte aktuální verzi. (Například pro Visual Studio 2017, vyberte v141.)  
  
4.  Sestavte řešení. Pokud se sestavení nezdaří, upravte nastavení a spusťte sestavení znovu.  
  
 Zdroje dat jsou obsaženy v samostatném databázovém projektu, takže lze snadněji upravovat a ladit procedury, které jsou v nich uloženy. Pokud upgradujete projekt jazyka C++, který obsahuje zdroje dat, automaticky se vytvoří samostatný databázový projekt.  
  
 Informace o tom, jak aktualizovat cílové verze Windows najdete v tématu [úprava WINVER a _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).  
  
## <a name="see-also"></a>Viz také  
 [Změny systému sestavení](../build/build-system-changes.md)  
 [Co je nového pro Visual C++ v aplikaci Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md) [historie 2003 2015 změn Visual C++](../porting/visual-cpp-change-history-2003-2015.md)   
 [Nestandardní chování](../cpp/nonstandard-behavior.md)