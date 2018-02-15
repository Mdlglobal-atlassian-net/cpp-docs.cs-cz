---
title: "Třídy (ATL) pro podporu systému Windows | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.atl.windows
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b64654f0f483ec401b379ec4c512489ce8cac823
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="windows-support-classes"></a>Třídy pro podporu systému Windows
Následující třídy poskytují podporu pro windows:  
  
-   [_U_MENUorID](../atl/reference/u-menuorid-class.md) poskytuje obálek pro **CreateWindow** a **CreateWindowEx**.  
  
-   [CWindow](../atl/reference/cwindow-class.md) obsahuje metody pro práci s časového období. `CWindow` je základní třídou pro `CWindowImpl`, `CDialogImpl`, a `CContainedWindow`.  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) implementuje okno založeno na třídě nové okno. Také umožňuje podtřídami nebo supertřídě okna.  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md) implementuje dialogové okno.  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) implementuje, dialogové okno (modální nebo nemodální), který hostuje ovládací prvky ActiveX.  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) implementuje dialogové okno (modální nebo nemodální) pomocí základních funkcí.  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) manipuluje okno, který je hostitelem ovládacího prvku ActiveX.  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) poskytuje metody pro manipulaci s okno, které hostuje ovládacího prvku ActiveX a má také podpora pro hostování licencované ovládací prvky ActiveX.  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) implementuje okno obsažené v rámci jiného objektu.  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) spravuje informace novou třídu okna.  
  
-   [CDynamicChain](../atl/reference/cdynamicchain-class.md) podporuje dynamické řetězení mapy zpráv.  
  
-   [CMessageMap](../atl/reference/cmessagemap-class.md) umožňuje objekt vystavit jeho zpráva se mapuje na jiné objekty.  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) poskytuje jednoduché metodu standardizace vlastnosti objektu ATL okno.  
  
-   [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) poskytuje výchozí hodnoty pro styly oken a rozšířené styly použít k vytvoření okna. Tyto hodnoty se přidají pomocí operátoru logické OR, hodnoty zadané během vytváření časového období.  
  
## <a name="related-articles"></a>Související články  
 [ATL – třídy oken](../atl/atl-window-classes.md)  
  
 [ATL – tutoriál](../atl/active-template-library-atl-tutorial.md)  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../atl/atl-class-overview.md)   
 [Makra Map zpráv](../atl/reference/message-map-macros-atl.md)   
 [Makra třídy okna](../atl/reference/window-class-macros.md)

