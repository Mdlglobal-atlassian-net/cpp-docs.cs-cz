---
title: "Redistribuce součástí s použitím slučovacích modulů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 14eb80452a9b5ceefeea7ff204c42288b7542c5a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="redistributing-components-by-using-merge-modules"></a>Redistribuce součástí s použitím modulů sloučení
Visual Studio obsahuje [slučovací moduly](http://msdn.microsoft.com/library/aa367434) pro každou součást Visual C++, který je licencován distribuována pomocí aplikace. Jakmile se slučovací modul zkompiluje v instalačním souboru Instalační služba systému Windows, umožňuje nasazení konkrétních knihoven DLL do počítačů na určité platformě. V instalačním souboru určete, že slučovací moduly představují požadavky pro vaši aplikaci. Při instalaci sady Visual Studio slučovacích modulů nainstalovaných v \Program Files\Common Files\Merge Modules\\. (Jenom bez ladění verze Visual C++ – knihovny DLL může distribuují.) Další informace a odkaz na seznam slučovací moduly, které jsou licencí pro redistribuci najdete v tématu [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
 Můžete povolit instalaci redistributable knihovny DLL jazyka Visual C++ do složky %SYSTEMROOT%\system32\ slučovacích modulů. (Visual Studio, samotné používá tato technika.) Instalace do této složky se však nezdaří, pokud daný uživatel nemá oprávnění správce.  
  
 Doporučujeme slučovací moduly nepoužívat, s výjimkou případů, kdy není nutné aplikaci obsluhovat a nemáte závislosti na více než jedné verzi knihovny DLL. Do jednoho instalačního programu nelze zahrnout slučovací moduly pro různé verze stejné knihovny DLL. Slučovací moduly navíc komplikují obsluhu knihoven DLL nezávisle na aplikaci. Místo toho doporučujeme nainstalovat distribuovatelného balíčku Visual C++.  
  
## <a name="see-also"></a>Viz také  
 [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md)