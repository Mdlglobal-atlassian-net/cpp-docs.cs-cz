---
title: Rozhraní MFC a knihovna ATL
ms.date: 01/24/2018
ms.assetid: 31b1a3a8-4154-4c4a-af10-fafc23ecdc5c
ms.topic: overview
ms.openlocfilehash: 3a58e68925fd77d002400bfe9d1f2bd28c60f78c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214328"
---
# <a name="mfc-and-atl"></a>Rozhraní MFC a knihovna ATL

Microsoft Foundation Classes (MFC) poskytuje C++ objektově orientovanou obálku v systému Win32 pro rychlý vývoj nativních aplikací klasické pracovní plochy. Knihovna ATL (Active Template Library) je Obálková knihovna, která zjednodušuje vývoj modelu COM a je často používána pro vytváření ovládacích prvků ActiveX.

Programy knihovny MFC nebo knihovny ATL můžete vytvořit pomocí sady Visual Studio Community Edition nebo vyšší. Edice Express nepodporují knihovnu MFC ani knihovnu ATL.

V aplikaci Visual Studio 2015 je C++ vizuál volitelnou komponentou a komponenty MFC a ATL jsou volitelné dílčí komponenty v rámci vizuálu C++. Pokud nevyberete tyto komponenty při první instalaci sady Visual Studio, budete vyzváni k jejich instalaci při prvním pokusu o vytvoření nebo otevření projektu knihovny MFC nebo ATL.

V aplikaci Visual Studio 2017 a novějších jsou knihovny MFC a ATL volitelné dílčí komponenty pod **vývojem pro C++ stolní počítače s** úlohou v instalační program pro Visual Studio programu. Můžete nainstalovat podporu knihovny ATL bez knihovny MFC nebo kombinované knihovny MFC a ATL (knihovna MFC závisí na knihovně ATL). Další informace o úlohách a komponentách najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="related-articles"></a>Související články

|Název|Popis|
|-----------|-----------------|
|[Desktopové aplikace knihovny MFC](../mfc/mfc-desktop-applications.md)|Microsoft Foundation Classes poskytuje obálku zaměřenou na tenké objekty v rámci Win32, který umožňuje rychlý vývoj C++aplikací GUI v nástroji.|
|[Desktopové komponenty ATL objektů COM](../atl/atl-com-desktop-components.md)|Knihovna ATL poskytuje šablony tříd a jiné konstrukce použití pro zjednodušení vytváření objektů modelu COM v C++nástroji.|
|[Sdílené třídy ATL/MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Odkazy na [třídy CStringT](../atl-mfc-shared/reference/cstringt-class.md) a další třídy, které jsou sdíleny pomocí knihovny MFC a knihovny ATL.|
|[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)|Editor prostředků umožňuje upravovat prostředky uživatelského rozhraní, jako jsou řetězce, obrázky a dialogová okna.|
|[C++ v sadě Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Nadřazené téma pro veškerý C++ obsah v knihovně MSDN.|
