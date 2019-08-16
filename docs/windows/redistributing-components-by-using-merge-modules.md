---
title: Redistribuce součástí s použitím modulů sloučení
ms.date: 11/04/2016
helpviewer_keywords:
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
ms.openlocfilehash: 36dc115987b051f117264991927c2599a88deda6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514769"
---
# <a name="redistributing-components-by-using-merge-modules"></a>Redistribuce součástí s použitím modulů sloučení

Visual Studio zahrnuje [slučovací moduly](/windows/win32/Msi/about-merge-modules) pro každou součást C++ vizuálu, která je licencovaná pro distribuci s aplikací. Jakmile se slučovací modul zkompiluje v instalačním souboru Instalační služba systému Windows, umožňuje nasazení konkrétních knihoven DLL do počítačů na určité platformě. V instalačním souboru určete, že slučovací moduly představují požadavky pro vaši aplikaci. Při instalaci sady Visual Studio jsou slučovací moduly nainstalovány v modulech\\\Program Files\Common Files\Merge. (Distribuovat lze pouze neladitelné verze C++ vizuálních knihoven DLL.) Další informace a odkaz na seznam slučovacích modulů, které jsou licencovány pro opětovnou distribuci, najdete v tématu [Redistribuce vizuálních C++ souborů](redistributing-visual-cpp-files.md).

Pomocí slučovacích modulů můžete povolit instalaci redistribuovatelných vizuálních C++ knihoven DLL do složky%SystemRoot%\system32\. (Tato technika používá aplikaci Visual Studio.) Instalace do této složky se však nezdaří, pokud daný uživatel nemá oprávnění správce.

Doporučujeme slučovací moduly nepoužívat, s výjimkou případů, kdy není nutné aplikaci obsluhovat a nemáte závislosti na více než jedné verzi knihovny DLL. Do jednoho instalačního programu nelze zahrnout slučovací moduly pro různé verze stejné knihovny DLL. Slučovací moduly navíc komplikují obsluhu knihoven DLL nezávisle na aplikaci. Místo toho doporučujeme nainstalovat vizuální C++ Distribuovatelný balíček.

## <a name="see-also"></a>Viz také:

[Redistribuce souborů Visual C++](redistributing-visual-cpp-files.md)
