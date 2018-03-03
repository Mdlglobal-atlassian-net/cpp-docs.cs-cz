---
title: MFC a knihovna ATL | Microsoft Docs
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 31b1a3a8-4154-4c4a-af10-fafc23ecdc5c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b863b002f6ab8362ed51e8cb16747de53eeb1b8
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="mfc-and-atl"></a>Rozhraní MFC a knihovna ATL
Microsoft Foundation třídy (MFC), poskytují obálku objektově orientované C++ přes Win32 pro rychlý vývoj nativních aplikací klasické pracovní plochy. Aktivní šablony Library (ATL) je obálky knihovny, která usnadňuje vývoj COM a se velmi často používá pro vytváření ovládacích prvků ActiveX.  
  
Můžete vytvořit MFC nebo ATL programy s Visual Studio Community Edition nebo vyšší. Edice Express nepodporují MFC nebo ATL. 

V sadě Visual Studio 2015 Visual C++ je volitelná součást a jsou volitelné dílčí součásti v jazyce Visual C++ MFC a knihovna ATL součásti. Pokud nevyberete těchto součástí při první instalaci sady Visual Studio, budete vyzváni k instalaci, je při prvním pokusu o vytvoření nebo otevření projektu knihovny MFC nebo ATL.  

Visual Studio 2017 a novější, MFC a knihovna ATL jsou volitelné dílčí součásti v části **vývoj aplikací s jazykem C++** úloh ve Visual Studio Instalační program. Můžete nainstalovat podporu ATL bez knihovny MFC nebo kombinaci Podpora MFC a knihovny ATL (MFC závisí na ATL). Další informace o pracovním zatížení a součásti najdete v tématu [nainstalovat Visual Studio 2017](/visualstudio/install/install-visual-studio).
  
## <a name="related-articles"></a>Související články  
  
|Název|Popis|  
|-----------|-----------------|  
|[Desktopové aplikace knihovny MFC](../mfc/mfc-desktop-applications.md)|Microsoft Foundation třídy poskytují dynamické objektově orientované obálku přes Win32 umožňující rychlý vývoj aplikací grafického uživatelského rozhraní v jazyce C++.|  
|[Desktopové komponenty ATL objektů COM](../atl/atl-com-desktop-components.md)|ATL poskytuje šablony třídy a jiné použití vytvoří pro zjednodušení vytváření objektů COM v jazyce C++.|  
|[ATL a MFC sdílené třídy](../atl-mfc-shared/atl-mfc-shared-classes.md)|Odkazuje pro [CStringT třída](../atl-mfc-shared/reference/cstringt-class.md) a jiné třídy, které jsou sdíleny MFC a ATL.|  
|[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)|Editor prostředků umožňuje upravit prostředkům uživatelského rozhraní, například řetězce, Image a dialogová okna.|  
|[Visual C++](../visual-cpp-in-visual-studio.md)|Nadřazené téma pro veškerý obsah C++ v knihovně MSDN.|