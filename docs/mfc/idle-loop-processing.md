---
title: Zpracování smyčky nečinnosti
ms.date: 11/04/2016
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
ms.openlocfilehash: 72491c057f3bf7c531bb5515b07f1e9d0acf35d5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508412"
---
# <a name="idle-loop-processing"></a>Zpracování smyčky nečinnosti

Mnoho aplikací provádí zdlouhavé zpracování "na pozadí". V některých případech se při použití multithreadingu pro takovou práci vykazuje výkon. Vlákna zahrnují dodatečné nároky na vývoj, takže se nedoporučují pro jednoduché úlohy, jako je například práce v době nečinnosti, kterou knihovna MFC provádí ve funkci [OnIdle](../mfc/reference/cwinthread-class.md#onidle) . Tento článek se zaměřuje na nečinné zpracování. Další informace o multithreading naleznete v tématu [témata](../parallel/multithreading-support-for-older-code-visual-cpp.md)s více vlákny.

Některé druhy zpracování na pozadí jsou vhodně provedeny v intervalech, které uživatel jinak nepracuje s aplikací. V aplikaci vyvinuté pro operační systém Microsoft Windows může aplikace provádět zpracování nečinným rozdělením zdlouhavého procesu do velkého množství malých fragmentů. Po zpracování každého fragmentu aplikace poskytne řízení spouštění systému Windows pomocí smyčky [PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) .

Tento článek vysvětluje dva způsoby, jak provádět nečinné zpracování v aplikaci:

- Použití **PeekMessage** v hlavní smyčce zpráv knihovny MFC.

- Vložení jiné smyčky **PeekMessage** někam jinam do aplikace.

##  <a name="_core_peekmessage_in_the_mfc_message_loop"></a>PeekMessage ve smyčce zpráv knihovny MFC

V aplikaci vyvinuté pomocí knihovny MFC obsahuje hlavní smyčka zpráv ve `CWinThread` třídě smyčku zpráv, která volá Win32 API [PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) . Tato smyčka také volá `OnIdle` členskou `CWinThread` funkci mezi zprávami. Aplikace může zpracovávat zprávy v této době nečinnosti přepsáním `OnIdle` funkce.

> [!NOTE]
>  `Run`, `OnIdle`a některé jiné členské funkce jsou nyní členy třídy `CWinThread` namísto třídy `CWinApp`. `CWinApp`je odvozen z `CWinThread`.

Další informace o provádění nečinného zpracování naleznete v tématu [OnIdle](../mfc/reference/cwinthread-class.md#onidle) v *Referenci knihovny MFC*.

##  <a name="_core_peekmessage_elsewhere_in_your_application"></a>PeekMessage jinde v aplikaci

Další metodou pro provádění nečinného zpracování v aplikaci je vložení smyčky zpráv do jedné z vašich funkcí. Tato smyčka zpráv je velmi podobná hlavní smyčce zpráv knihovny MFC, která se nachází v okruhu [CWinThread:: Run](../mfc/reference/cwinthread-class.md#run). To znamená, že taková smyčka v aplikaci vyvinutá pomocí knihovny MFC musí provádět mnoho stejných funkcí jako hlavní smyčka zpráv. Následující fragment kódu ukazuje zápis do smyčky zpráv, která je kompatibilní s knihovnou MFC:

[!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]

Tento kód vložený do funkce, cykly, dokud je zpracování nečinné. V rámci této smyčky vnořená smyčka opakovaně `PeekMessage`volá. Pokud volání vrátí nenulovou hodnotu, volá `CWinThread::PumpMessage` smyčka k provedení normálního překladu zpráv a odeslání. I `PumpMessage` když je nedokumentované, můžete si prohlédnout svůj zdrojový kód v souboru ThrdCore. cpp v adresáři \atlmfc\src\mfc instalace Visual C++ .

Jakmile vnitřní smyčka skončí, vnější smyčka provede nečinné zpracování s jedním nebo více voláními `OnIdle`. První volání je pro účely knihovny MFC. Můžete provést další volání `OnIdle` na vlastní práci na pozadí.

Další informace o provádění nečinného zpracování naleznete [](../mfc/reference/cwinthread-class.md#onidle) v tématu nečinné v odkazu knihovny MFC.

## <a name="see-also"></a>Viz také:

[Obecná témata MFC](../mfc/general-mfc-topics.md)
