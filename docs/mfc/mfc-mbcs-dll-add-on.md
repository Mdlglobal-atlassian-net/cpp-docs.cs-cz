---
title: MFC MBCS DLL – doplněk
ms.date: 12/02/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: fe74e0639664b6a6a86a4c3269f174de441002f4
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810366"
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL – doplněk

Podpora pro MFC a jeho knihovny vícebajtových znakových sad (MBCS) vyžaduje další krok během instalace sady Visual Studio v Visual Studio 2013 a novějším.

**Visual Studio 2013**: knihovny MFC nainstalované Visual Studio 2013 ve výchozím nastavení podporují pouze vývoj pro Unicode. Knihovny DLL znakové sady MBCS budete potřebovat pro sestavení projektu MFC v Visual Studio 2013, který má vlastnost **znaková sada** nastavenou na **použití vícebajtové znakové sady** nebo **není nastavena**. Stáhněte si knihovnu DLL na [vícebajtové knihovně MFC pro Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770).

**Visual Studio 2015**: knihovny MFC DLL pro kódování Unicode a MBCS jsou součástí komponent C++ Visual Setup, ale podpora knihovny MFC není ve výchozím nastavení nainstalovaná. Visual C++ a MFC jsou volitelné konfigurace instalace v instalačním programu sady Visual Studio. Chcete-li se ujistit, že je nainstalována knihovna MFC, zvolte možnost **vlastní** v nastavení a v části **programovací jazyky**ověřte, zda jsou vybrány možnosti **Visual C++**  a **Microsoft Foundation Classes pro C++**  . Pokud jste již nainstalovali aplikaci Visual Studio, budete vyzváni k instalaci sady Visual C++ and/nebo knihovny MFC při pokusu o vytvoření projektu knihovny MFC.

**Visual Studio 2017 a novější**: knihovny MFC DLL pro Unicode a MBCS se nainstalují s funkcí **vývoj C++ pro desktopy s** úlohou při výběru **podpory MFC a ATL** z podokna **volitelné komponenty** v instalační program pro Visual Studio programu. Pokud vaše instalace tyto komponenty neobsahuje, přejděte do **souboru | Otevřete dialog nové projekty** a klikněte na odkaz **otevřít instalační program pro Visual Studio** . Další informace najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="see-also"></a>Viz také:

[MFC – knihovní verze](../mfc/mfc-library-versions.md)
