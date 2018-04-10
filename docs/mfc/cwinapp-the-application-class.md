---
title: CWinApp – Třída aplikace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- application class [MFC]
- CWinApp class [MFC], CWinThread
- MFC, WinMain and
- CWinApp class [MFC], multithreading
- CWinThread class [MFC], and CWinApp
- InitApplication method [MFC]
- WinMain method [MFC]
- WinMain method [MFC], in MFC
- CWinApp class [MFC], WinMain
ms.assetid: 935822bb-d463-481b-a5f6-9719d68ed1d5
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c1f146df2dd4f97affdaf1c3107d1b00bfd86876
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cwinapp-the-application-class"></a>CWinApp – třída aplikace
Třída hlavní aplikace v prostředí MFC zapouzdří inicializace, spuštění a ukončení aplikace pro operační systém Windows. Aplikace založená na rozhraní musí mít jeden a pouze jeden objekt třídy odvozené z [CWinApp](../mfc/reference/cwinapp-class.md). Tento objekt je vytvořený, před vytvořením systému windows.  
  
 `CWinApp`je odvozený od `CWinThread`, která představuje hlavní vlákno spuštění vaší aplikaci, což může mít jeden nebo více vláken. V nejnovější verze knihovny MFC `InitInstance`, **spustit**, `ExitInstance`, a `OnIdle` členské funkce jsou ve skutečnosti ve třídě `CWinThread`. Tyto funkce jsou popsány zde, jako kdyby byly `CWinApp` členy místo, protože se týká objektu role jako objekt aplikace a nikoli jako primární vlákno.  
  
> [!NOTE]
>  Třídě aplikace se považuje za primární vlákno spuštění vaší aplikace. Pomocí funkce rozhraní API Win32, můžete také vytvořit sekundární vláken provádění. Knihovny MFC můžete použít tyto vláken. Další informace najdete v tématu [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 Stejně jako žádné program pro operační systém Windows má aplikace framework `WinMain` funkce. V aplikaci framework, ale můžete Nezapisovat `WinMain`. To poskytuje knihovny tříd a je volána při spuštění aplikace. `WinMain`provede standardní služby, jako je registrace tříd oken. Potom zavolá členské funkce objektu aplikace k inicializaci a spuštění aplikace. (Můžete přizpůsobit `WinMain` přepsáním `CWinApp` členské funkce, která `WinMain` volání.)  
  
 Inicializace aplikace, `WinMain` volání objektu application `InitApplication` a `InitInstance` členské funkce. Ke spuštění aplikace ve smyčce zpráv, `WinMain` volání **spustit** – členská funkce. Na ukončení `WinMain` volání objektu application `ExitInstance` – členská funkce.  
  
> [!NOTE]
>  Názvy jako v **tučné** v této dokumentaci znamenat elementy poskytl Microsoft Foundation Class Library a Visual C++. Názvy jako v `monospaced` typu znamenat prvky, které můžete vytvořit ani přepsat.  
  
## <a name="see-also"></a>Viz také  
 [Obecná témata MFC](../mfc/general-mfc-topics.md)   
 [CWinApp a Průvodce aplikací MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)   
 [Přepisovatelné členské funkce CWinApp](../mfc/overridable-cwinapp-member-functions.md)   
 [Speciální služby CWinApp](../mfc/special-cwinapp-services.md)

