---
title: "Zpracování smyčky nečinnosti | Microsoft Docs"
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
- MFC, background processing
- PeekMessage method [MFC], elsewhere than message loop
- PeekMessage method [MFC]
- MFC, messages
- messages [MFC], loops
- OnIdle method [MFC]
- processing [MFC], background
- idle loop processing [MFC]
- idle processing [MFC]
- threading [MFC], alternatives to multithreading
- processing, during idle loop
- processing [MFC]
- background processing [MFC]
ms.assetid: 5c7c46c1-6107-4304-895f-480983bb1e44
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: baabba60ffaf886b7a34acfbff5b923a4495fa1b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="idle-loop-processing"></a>Zpracování smyčky nečinnosti
Mnoho aplikací provádět zdlouhavé zpracování "v pozadí." Faktory ovlivňující výkon někdy určují používání více vláken pro takové práce. Vlákna zahrnují režijní náklady na vývoj navíc, proto se doporučuje pro jednoduché úlohy, jako je pracovní doby nečinnosti, která MFC v [OnIdle](../mfc/reference/cwinthread-class.md#onidle) funkce. Tento článek se zaměřuje na zpracování při nečinnosti. Další informace o více vláken, viz [Multithreading témata](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 Některé druhy zpracování na pozadí správně hotovi během intervalů, které uživatel není jinak interakci s aplikací. V aplikaci vytvořených pro operační systém Microsoft Windows můžete aplikaci provádět zpracování doby nečinnosti rozdělením trvat poměrně dlouho do mnoho malých fragmenty. Po zpracování každý fragment, vypočítá aplikace řízení provádění pomocí systému Windows [PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943) smyčky.  
  
 Tento článek vysvětluje dva způsoby, jak nečinnosti zpracování ve vaší aplikaci:  
  
-   Pomocí **PeekMessage** ve smyčce zpráv knihovny MFC.  
  
-   Vložení jiné **PeekMessage** cykly jinde v aplikaci.  
  
##  <a name="_core_peekmessage_in_the_mfc_message_loop"></a>PeekMessage ve smyčce zpráv knihovny MFC  
 V aplikaci vyvinuté pomocí MFC, hlavní zpráva smyčky v `CWinThread` třída obsahuje smyčku zpráva, která volá [PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943) Win32 API. Cykly také volání `OnIdle` členské funkce `CWinThread` mezi zprávy. Aplikace může zpracovat zprávy v tento čas nečinnosti přepsáním `OnIdle` funkce.  
  
> [!NOTE]
>  **Spustit**, `OnIdle`, a některé další členské funkce jsou nyní členy třídy `CWinThread` spíše než třídy `CWinApp`. `CWinApp`je odvozený od `CWinThread`.  
  
 Další informace o provádění zpracování při nečinnosti najdete v tématu [OnIdle](../mfc/reference/cwinthread-class.md#onidle) v *odkaz knihovny MFC*.  
  
##  <a name="_core_peekmessage_elsewhere_in_your_application"></a>PeekMessage jinde v aplikaci  
 Další možností pro provádění nečinnosti zpracování v aplikaci, je vložení smyčku zpráv v jednom z funkcí. Tato zpráva smyčky je velmi podobný smyčka hlavní zpráv knihovny MFC, najít v [CWinThread::Run](../mfc/reference/cwinthread-class.md#run). To znamená, smyčky v aplikace vyvinuté pomocí MFC musí provádět spoustu stejné funkce jako hlavní zpráva smyčky. Následující fragment kódu ukazuje zpráva smyčky, který je kompatibilní s knihovnou MFC:  
  
 [!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]  
  
 Tento kód vložený ve funkci, v cyklu, dokud je zpracování při nečinnosti udělat. V rámci této smyčky smyčku vnořené opakovaně volá **PeekMessage**. Tak dlouho, dokud toto volání se vrátí nenulovou hodnotu, že opakování ve smyčce volá `CWinThread::PumpMessage` provádět překlad normální zpráva a odeslání. I když `PumpMessage` nedokumentovanými, můžete zkontrolovat jeho zdrojový kód v souboru ThrdCore.Cpp v adresáři \atlmfc\src\mfc instalace Visual C++.  
  
 Po skončení vnitřní smyčky vnější smyčky provádí zpracování při nečinnosti pomocí jednoho nebo více volání `OnIdle`. První volání je pro účely MFC společnosti. Můžete provést další volání do `OnIdle` práci vlastní pozadí.  
  
 Další informace o provádění zpracování při nečinnosti najdete v tématu [OnIdle](../mfc/reference/cwinthread-class.md#onidle) v referenční příručka knihovny MFC.  
  
## <a name="see-also"></a>Viz také  
 [Obecná témata MFC](../mfc/general-mfc-topics.md)

