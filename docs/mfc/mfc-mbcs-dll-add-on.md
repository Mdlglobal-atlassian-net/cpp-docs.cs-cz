---
title: MFC MBCS DLL – doplněk
ms.date: 05/08/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: 20145b200a0f8bac8ccb461331d4d233a3b0251e
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524821"
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL – doplněk

Podpora knihovny MFC a knihovny vícebajtovou znakovou sadu (MBCS) vyžaduje další krok při instalaci sady Visual Studio v sadě Visual Studio 2013 nebo novější.

**Visual Studio 2013**: Ve výchozím nastavení podporují pouze knihovny MFC, nainstalovaná v sadě Visual Studio 2013 vývoj kódování Unicode. Knihovny DLL znakové sady MBCS je nutné k vytvoření projektu knihovny MFC v sadě Visual Studio 2013, který má **znaková sada** vlastnost nastavena na hodnotu **použít vícebajtovou znakovou sadu** nebo **Nenastaveno**. Stáhněte si knihovny DLL v [vícebajtová knihovna MFC pro sadu Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770).

**Visual Studio 2015**: Kódování Unicode a MBCS MFC DLL jsou součástí instalace součásti Visual C++, ale podpora knihovny MFC není nainstalovaný ve výchozím nastavení. Visual C++ a knihovnou MFC jsou konfigurace volitelná instalace v instalačním programu sady Visual Studio. Chcete-li mít jistotu, že je nainstalovaná knihovny MFC, zvolte **vlastní** v instalačním programu a v části **programovací jazyky**, ujistěte se, že **Visual C++** a **Microsoft Foundation Třídy jazyka C++** jsou vybrány. Pokud jste již nainstalovali Visual Studio, budete vyzváni k instalaci Visual C++ a/nebo knihovny MFC, při pokusu o vytvoření projektu knihovny MFC.

**Visual Studio 2017 a novější**: Kódování Unicode a MBCS MFC DLL se instalují s **vývoj desktopových aplikací pomocí C++** zatížení při výběru **podporu knihovny MFC a ATL** z **volitelné součásti** podokně. Pokud není instalace těchto součástí, přejděte **soubor | Nové projekty** dialogové okno a kliknutím **otevřít instalační program Visual Studio** odkaz.

## <a name="see-also"></a>Viz také:

[MFC – knihovní verze](../mfc/mfc-library-versions.md)
