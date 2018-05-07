---
title: Aplikací a vláken podporují třídy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.support
dev_langs:
- C++
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9f3877cf85e369756b15d565af1481fd6d258df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="application-and-thread-support-classes"></a>Třídy pro podporu aplikací a vláken
Každá aplikace má pouze jeden objekt aplikace; Tento objekt koordinuje jiných objektů nástroje spuštěným programem a je odvozený od `CWinApp`.  
  
 Knihovna Microsoft Foundation Class (MFC) podporuje více vláken provádění v rámci aplikace. Všechny aplikace musí mít alespoň jedno vlákno; vlákno používané vaší `CWinApp` tento primární podproces je objekt.  
  
 `CWinThread` zapouzdří část vláken funkcí operačního systému. Chcete-li pomocí více vláken jednodušší, MFC také poskytuje synchronizace objekt třídy k poskytnutí rozhraní C++ do Win32 synchronizačními objekty.  
  
## <a name="application-and-thread-classes"></a>Třídy aplikací a vláken  
 [CWinApp](../mfc/reference/cwinapp-class.md)  
 Zapouzdří kód inicializujte, spuštění a ukončení aplikace. Objekt vaše aplikace bude odvozovat z této třídy.  
  
 [CWinThread](../mfc/reference/cwinthread-class.md)  
 Základní třída pro všechna vlákna. Použít přímo, nebo odvození třídy z `CWinThread` Pokud vaše vlákno provádí funkce uživatelského rozhraní. `CWinApp` je odvozený od `CWinThread`.  
  
## <a name="synchronization-object-classes"></a>Objekt třídy synchronizace  
 [CSyncObject](../mfc/reference/csyncobject-class.md)  
 Základní třída třídy objekt synchronizace.  
  
 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
 Třída synchronizace, která umožňuje pouze jedno vlákno v rámci jednoho procesu přístupu k objektu.  
  
 [Prohlížení](../mfc/reference/csemaphore-class.md)  
 Třída synchronizace, která umožňuje od jedné do stanovený maximální počet souběžných přístupů k objektu.  
  
 [CMutex](../mfc/reference/cmutex-class.md)  
 Třída synchronizace, která umožňuje pouze jedno vlákno v rámci libovolný počet procesů přístup k objektu.  
  
 [CEvent](../mfc/reference/cevent-class.md)  
 Třída synchronizace, která upozorní aplikace, když došlo k události.  
  
 [CSingleLock](../mfc/reference/csinglelock-class.md)  
 Použitý v členské funkce tříd bezpečného přístupu k uzamčení na jeden objekt synchronizace.  
  
 [CMultiLock](../mfc/reference/cmultilock-class.md)  
 Použitý v členské funkce tříd vláken k uzamčení na jeden nebo více objektů synchronizace z pole objektů synchronizace.  
  
## <a name="related-classes"></a>Související třídy  
 [CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)  
 Analyzuje příkazového řádku, pomocí kterého byl váš program spuštěn.  
  
 [CWaitCursor](../mfc/reference/cwaitcursor-class.md)  
 Vloží kurzoru čekání na obrazovce. Použitá při náročná operace.  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 Zpracovává trvalé úložiště dat o stavu pro ovládací pruhy ukotvení.  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 Udržuje naposledy použité seznamu souborů (naposledy použitých).  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

