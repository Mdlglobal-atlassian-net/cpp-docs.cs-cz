---
title: Rozhraní MFC a knihovna ATL
ms.date: 01/24/2018
ms.assetid: 31b1a3a8-4154-4c4a-af10-fafc23ecdc5c
ms.openlocfilehash: 620d514e1bc1bad6c33eab16577639c4053cdf10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486356"
---
# <a name="mfc-and-atl"></a>Rozhraní MFC a knihovna ATL

Microsoft Foundation Classes (MFC) poskytuje objektově orientovanou obálku C++ přes Win32 pro rychlý vývoj nativních aplikací klasické pracovní plochy. Aktivní šablony knihovny (ATL) je obálka knihovnu, která zjednodušuje vývoj COM a je používána pro vytváření ovládacích prvků ActiveX.

Můžete vytvořit programy MFC nebo ATL s Visual Studio Community Edition nebo vyšší. Edice Express nepodporuje MFC ani ATL.

V sadě Visual Studio 2015 Visual C++ je volitelnou komponentou a komponent knihovny MFC a ATL jsou volitelné dílčí komponenty v jazyce Visual C++. Pokud nevyberete tyto součásti při první instalaci sady Visual Studio, budete vyzváni k instalaci je při prvním pokusu o vytvoření nebo otevření projektu knihovny MFC nebo ATL.

V sadě Visual Studio 2017 a novější knihovny MFC a ATL jsou volitelné dílčí komponenty pod **vývoj desktopových aplikací pomocí C++** úlohy v aplikaci instalační program sady Visual Studio. Můžete nainstalovat podporu ATL bez knihovny MFC nebo knihovny MFC a ATL – podpora (MFC závisí na ATL) v kombinaci. Další informace o úlohách a komponentách najdete v tématu [instalace sady Visual Studio 2017](/visualstudio/install/install-visual-studio).

## <a name="related-articles"></a>Související články

|Název|Popis|
|-----------|-----------------|
|[Desktopové aplikace knihovny MFC](../mfc/mfc-desktop-applications.md)|Microsoft Foundation Classes poskytuje obálku dynamického zajišťování objektově orientované přes Win32, který umožňuje rychlý vývoj aplikací GUI v jazyce C++.|
|[Desktopové komponenty ATL objektů COM](../atl/atl-com-desktop-components.md)|Knihovna ATL poskytuje šablony tříd a konstrukce pro zjednodušení vytváření objektů modelu COM v jazyce C++ jiné použití.|
|[Sdílené třídy ATL/MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Odkazy [cstringt – třída](../atl-mfc-shared/reference/cstringt-class.md) a jiné třídy, které jsou sdílené mezi MFC a ATL.|
|[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)|Editor prostředků umožňuje upravovat prostředky uživatelského prostředí, jako jsou řetězce, obrázky a dialogových oknech.|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Nadřazené téma pro veškerý obsah jazyka C++ v knihovně MSDN.|