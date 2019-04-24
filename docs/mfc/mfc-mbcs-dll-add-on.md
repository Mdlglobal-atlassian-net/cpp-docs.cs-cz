---
title: MFC MBCS DLL – doplněk
ms.date: 1/04/2018
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: 2fdbb5dd862c7d1a8845813c6234fea9e902c1f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62238526"
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL – doplněk

Podpora knihovny MFC a knihovny vícebajtovou znakovou sadu (MBCS) během instalace sady Visual Studio v sadě Visual Studio 2013, 2015 a 2017 vyžaduje další krok.

**Visual Studio 2013**: Ve výchozím nastavení podporují pouze knihovny MFC, nainstalovaná v sadě Visual Studio 2013 vývoj kódování Unicode. Knihovny DLL znakové sady MBCS je nutné k vytvoření projektu knihovny MFC v sadě Visual Studio 2013, který má **znaková sada** vlastnost nastavena na hodnotu **použít vícebajtovou znakovou sadu** nebo **Nenastaveno**. Stáhněte si knihovny DLL v [vícebajtová knihovna MFC pro sadu Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770).

**Visual Studio 2015**: Kódování Unicode a MBCS MFC DLL jsou součástí instalace součásti Visual C++, ale podpora knihovny MFC není nainstalovaný ve výchozím nastavení. Visual C++ a knihovnou MFC jsou konfigurace volitelná instalace v instalačním programu sady Visual Studio. Chcete-li mít jistotu, že je nainstalovaná knihovny MFC, zvolte **vlastní** v instalačním programu a v části **programovací jazyky**, ujistěte se, že **Visual C++** a **Microsoft Foundation Třídy jazyka C++** jsou vybrány. Pokud jste již nainstalovali Visual Studio, budete vyzváni k instalaci Visual C++ a/nebo knihovny MFC, při pokusu o vytvoření projektu knihovny MFC.

**Visual Studio 2017**: Kódování Unicode a MBCS MFC DLL se instalují s **vývoj desktopových aplikací pomocí C++** zatížení při výběru **podporu knihovny MFC a ATL** z **volitelné součásti** podokně. Pokud není instalace těchto součástí, přejděte **soubor | Nové projekty** dialogové okno a kliknutím **otevřít instalační program Visual Studio** odkaz.

## <a name="see-also"></a>Viz také:

[MFC – knihovní verze](../mfc/mfc-library-versions.md)
