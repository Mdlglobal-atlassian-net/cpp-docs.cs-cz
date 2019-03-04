---
title: Třídy pro podporu aplikací a vláken
ms.date: 11/04/2016
f1_keywords:
- vc.classes.support
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
ms.openlocfilehash: 667725a60fb0c907a9c2d017674f9d097d1f4946
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262035"
---
# <a name="application-and-thread-support-classes"></a>Třídy pro podporu aplikací a vláken

Každá aplikace má pouze jeden objekt aplikace; Tento objekt koordinuje ostatní objekty v běžící aplikaci a je odvozen z `CWinApp`.

Knihovny Microsoft Foundation Class (MFC) podporuje více vláken, která v rámci aplikace. Všechny aplikace musí mít alespoň jednoho vlákna; vlákno, které používá vaše `CWinApp` toto primární vlákno je objekt.

`CWinThread` zapouzdřuje část dělení na vlákna funkce operačního systému. Chcete-li používání více vláken jednodušší, MFC také poskytuje synchronizace objektu třídy, které poskytují rozhraní C++ Win32 synchronizace objektů.

## <a name="application-and-thread-classes"></a>Třídy aplikací a vláken

[CWinApp](../mfc/reference/cwinapp-class.md)<br/>
Zapouzdřuje kód pro inicializaci, spuštění a ukončení aplikace. Aplikační objekt bude odvozovat z této třídy.

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
Základní třída pro všechna vlákna. Přímo použít nebo odvodit třídu z `CWinThread` Pokud vašeho vlákna provádí funkce uživatelského rozhraní. `CWinApp` je odvozen z `CWinThread`.

## <a name="synchronization-object-classes"></a>Třídy synchronizace objektů

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
Základní třída synchronizační objekt třídy.

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
Synchronizační třídu, která umožňuje pouze jedno vlákno v rámci jediného procesu, aby přístup k objektu.

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
Synchronizační třídu, která umožňuje od jedné do zadané maximální počet souběžných přístupů na objekt.

[CMutex](../mfc/reference/cmutex-class.md)<br/>
Synchronizační třídu, která umožňuje pouze jedno vlákno v rámci libovolný počet procesů pro přístup k objektu.

[CEvent](../mfc/reference/cevent-class.md)<br/>
Třída synchronizace, která upozorní aplikaci, když došlo k události.

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
K uzamčení na jeden objekt synchronizace používají v členské funkce třídy bezpečné pro vlákna.

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
Použít v členské funkce třídy bezpečné pro vlákna k uzamčení na jeden nebo více objektů synchronizace z pole synchronizace objektů.

## <a name="related-classes"></a>Související třídy

[CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)<br/>
Analyzuje příkazového řádku, se kterým byl program spuštěn.

[CWaitCursor](../mfc/reference/cwaitcursor-class.md)<br/>
Umístí kurzor pro čekání na obrazovce. Používá se při dlouhé operace.

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
Zpracovává ukotvení data o stavu pro ovládacích pruhů trvalého úložiště.

[CRecentFileList](../mfc/reference/crecentfilelist-class.md)<br/>
Uchovává poslední použitou seznam souborů (MRU).

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
