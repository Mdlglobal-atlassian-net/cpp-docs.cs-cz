---
title: Redistribuce součástí s použitím modulů sloučení
ms.date: 11/04/2016
helpviewer_keywords:
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
ms.openlocfilehash: 7a110826e21f33986d68dcd46417ec5cbd5171bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362239"
---
# <a name="redistributing-components-by-using-merge-modules"></a>Redistribuce součástí s použitím modulů sloučení

Visual Studio obsahuje [slučovací moduly](/windows/desktop/Msi/about-merge-modules) pro každou komponentu jazyka Visual C++, které se licencuje znovu distribuovat s aplikací. Jakmile se slučovací modul zkompiluje v instalačním souboru Instalační služba systému Windows, umožňuje nasazení konkrétních knihoven DLL do počítačů na určité platformě. V instalačním souboru určete, že slučovací moduly představují požadavky pro vaši aplikaci. Při instalaci sady Visual Studio slučovací moduly jsou nainstalovány do \Program Files\Common moduly\\. (Pouze neladitelné verze knihoven DLL Visual C++ může být znovu distribuovány.) Další informace a odkaz na seznam slučovacích modulů, které jsou licencovány pro distribuci, naleznete v tématu [Redistribuce souborů Visual C++](redistributing-visual-cpp-files.md).

Slučovací moduly můžete použít k instalaci distribuovatelné součásti Visual C++ knihoven DLL do složky %SYSTEMROOT%\system32\. (Samotnou sadu visual Studio používá tuto techniku.) Instalace do této složky se však nezdaří, pokud daný uživatel nemá oprávnění správce.

Doporučujeme slučovací moduly nepoužívat, s výjimkou případů, kdy není nutné aplikaci obsluhovat a nemáte závislosti na více než jedné verzi knihovny DLL. Do jednoho instalačního programu nelze zahrnout slučovací moduly pro různé verze stejné knihovny DLL. Slučovací moduly navíc komplikují obsluhu knihoven DLL nezávisle na aplikaci. Namísto toho doporučujeme nainstalovat Distribuovatelný balíček Visual C++.

## <a name="see-also"></a>Viz také:

[Redistribuce souborů Visual C++](redistributing-visual-cpp-files.md)
