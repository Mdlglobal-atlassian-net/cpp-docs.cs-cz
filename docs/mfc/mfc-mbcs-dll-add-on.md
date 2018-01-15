---
title: "MFC MBCS DLL – doplněk | Microsoft Docs"
ms.custom: 
ms.date: 1/04/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MBCS
- MFC
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6f134110ff95956cc37d6e038a680ff27cbc298
ms.sourcegitcommit: 56f6fce7d80e4f61d45752f4c8512e4ef0453e58
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/12/2018
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL – doplněk

Podpora MFC a knihovny jeho vícebajtové znakové sady MBCS vyžaduje další krok při instalaci sady Visual Studio ve Visual Studiu 2013 se 2015 a 2017.

**Visual Studio 2013**: ve výchozím nastavení, knihovny MFC nainstalován v sadě Visual Studio 2013 podporují pouze vývoj kódování Unicode. Potřebujete MBCS dll k sestavení projektu knihovny MFC ve Visual Studiu 2013, který má **znaková sada** vlastnost nastavena na hodnotu **použití vícebajtové znakové sady** nebo **není nastavena**. Stáhnout knihovny DLL na [vícebajtové MFC knihovny pro Visual Studio 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40770).

**Visual Studio 2015**: jak kódování Unicode a MBCS MFC – knihovny DLL jsou součástí Visual C++ součástí instalace, ale podpora MFC není nainstalována ve výchozím nastavení. Visual C++ a rozhraní MFC jsou volitelné instalace konfigurace v instalačním programu sady Visual Studio. Chcete-li mít jistotu, že je nainstalována MFC, zvolte **vlastní** v instalačním programu a v části **programovací jazyky**, ujistěte se, že **Visual C++** a **Microsoft Foundation Třídy pro jazyk C++** jsou vybrány. Pokud jste již nainstalovali Visual Studio, budete vyzváni k instalaci Visual C++ nebo MFC, při pokusu o vytvoření projektu knihovny MFC.

**Visual Studio 2017**: kódování Unicode a MBCS MFC – knihovny DLL, které jsou nainstalovány s **vývoj aplikací s jazykem C++** zatížení při výběru **MFC a knihovna ATL podporují** z  **Volitelné součásti** podokně. Pokud vaše instalace neobsahuje tyto součásti, můžete spustit instalační program z **nové projekty** dialogové okno pomocí **otevřete instalační program Visual Studio** odkaz.

## <a name="see-also"></a>Viz také

[MFC – knihovní verze](../mfc/mfc-library-versions.md)

