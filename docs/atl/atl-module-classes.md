---
title: "ATL – třídy modulů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b254edfe75cfcdaee7ab15351f7c05c3d163e301
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="atl-module-classes"></a>ATL – třídy modulů
Toto téma popisuje modul třídy, které byly nové v ATL 7.0.  
  
## <a name="ccommodule-replacement-classes"></a>CComModule nahrazení třídy  
 Starší verze knihovny ATL používá `CComModule`. Ve ATL 7.0 `CComModule` funkce nahrazuje několik tříd:  
  
-   [CAtlBaseModule](../atl/reference/catlbasemodule-class.md) obsahuje informace o požadovaných většina aplikací, které používají knihovnu ATL. Obsahuje HINSTANCE modul a instance prostředku.  
  
-   [CAtlComModule](../atl/reference/catlcommodule-class.md) obsahuje informace, které vyžadují třídy COM v ATL.  
  
-   [CAtlWinModule](../atl/reference/catlwinmodule-class.md) obsahuje informace, které vyžadují oddílová třídy v ATL.  
  
-   [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) obsahuje podporu pro ladění v rozhraní.  
  
-   [CAtlModule](../atl/reference/catlmodule-class.md) následující `CAtlModule`-odvozené třídy jsou přizpůsobené tak, aby obsahovala informace vyžadované v konkrétní aplikaci typu. Většina členů v těchto tříd lze přepsat:  
  
    -   [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) používat v aplikacích knihovny DLL. Poskytuje kód pro standardní export.  
  
    -   [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) používat v aplikacích EXE. Poskytuje kód potřebné v EXE.  
  
    -   [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) poskytuje podporu pro vytvoření systému Windows NT a služby systému Windows 2000.  
  
 `CComModule`je stále k dispozici z důvodu zpětné kompatibility.  
  
## <a name="reasons-for-distributing-ccommodule-functionality"></a>Důvody pro distribuci CComModule funkce  
 Funkce `CComModule` byl distribuován do více tříd nové z následujících důvodů:  
  
-   Ujistěte se, funkce v `CComModule` přesná.  
  
     Podpora COM, oddílová, ladění v rozhraní a funkce specifické pro aplikaci (DLL nebo EXE) je nyní v samostatné třídy.  
  
-   Automaticky deklarujte globální instance každé z těchto modulů.  
  
     Globální instance třídy požadované modulu propojená do projektu.  
  
-   Odeberte nezbytné volání metody Init a termín.  
  
     Metody Init a termín byl přesunut do konstruktory a destruktory pro modul třídy; již není potřeba volat Init a termín.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../atl/active-template-library-atl-concepts.md)   
 [Přehled třídy](../atl/atl-class-overview.md)

