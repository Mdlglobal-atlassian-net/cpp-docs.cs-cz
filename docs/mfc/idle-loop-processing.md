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
ms.openlocfilehash: 9579d4bb8768b0227453af401d6fdc8a8bd482b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376016"
---
# <a name="idle-loop-processing"></a>Zpracování smyčky nečinnosti

Mnoho aplikací provádět zdlouhavé zpracování "na pozadí." Někdy výkon úvahy diktovat pomocí multithreading pro tuto práci. Vlákna zahrnují další režie vývoje, takže se nedoporučuje pro jednoduché úkoly, jako je práce nečinnosti, které provádí knihovna MFC ve funkci [OnIdle.](../mfc/reference/cwinthread-class.md#onidle) Tento článek se zaměřuje na nečinné zpracování. Další informace o multithreadingu naleznete v [tématu Témata s více vlákny](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Některé druhy zpracování na pozadí jsou vhodně prováděny v intervalech, které uživatel není jinak interakci s aplikací. V aplikaci vyvinuté pro operační systém Microsoft Windows může aplikace provádět zpracování nečinnosti rozdělením zdlouhavého procesu na mnoho malých fragmentů. Po zpracování každého fragmentu aplikace poskytuje ovládací prvek spuštění systému Windows pomocí smyčky [PeekMessage.](/windows/win32/api/winuser/nf-winuser-peekmessagew)

Tento článek vysvětluje dva způsoby, jak provést nečinné zpracování v aplikaci:

- Použití **PeekMessage** v hlavní smyčce zpráv knihovny MFC.

- Vkládání jiné **PeekMessage** smyčky někde jinde v aplikaci.

## <a name="peekmessage-in-the-mfc-message-loop"></a><a name="_core_peekmessage_in_the_mfc_message_loop"></a>Zpráva PeekMessage ve smyčce zpráv knihovny MFC

V aplikaci vyvinuté pomocí knihovny MFC `CWinThread` obsahuje smyčka hlavní zprávy ve třídě smyčku zpráv, která volá rozhraní API [Win32 služby PeekMessage.](/windows/win32/api/winuser/nf-winuser-peekmessagew) Tato smyčka také `OnIdle` volá `CWinThread` členská funkce mezi zprávami. Aplikace může zpracovávat zprávy v této `OnIdle` době nečinnosti přepsáním funkce.

> [!NOTE]
> `Run`, `OnIdle`a některé další členské funkce `CWinThread` jsou nyní `CWinApp`členy třídy spíše než třídy . `CWinApp`je odvozen `CWinThread`od .

Další informace o provádění nečinnosti zpracování naleznete v tématu [OnIdle](../mfc/reference/cwinthread-class.md#onidle) v *referenční knihovny MFC*.

## <a name="peekmessage-elsewhere-in-your-application"></a><a name="_core_peekmessage_elsewhere_in_your_application"></a>PeekMessage jinde ve vaší aplikaci

Další metoda pro provádění nečinné zpracování v aplikaci zahrnuje vložení smyčky zpráv v jedné z vašich funkcí. Tato smyčka zpráv je velmi podobná smyčce hlavní zprávy knihovny MFC, která se nachází v [cwinthread::Run](../mfc/reference/cwinthread-class.md#run). To znamená, že taková smyčka v aplikaci vyvinuté s knihovnou MFC musí provádět mnoho stejných funkcí jako hlavní smyčka zpráv. Následující fragment kódu ukazuje zápis smyčky zpráv, která je kompatibilní s knihovnou MFC:

[!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]

Tento kód, vložené do funkce, smyčky tak dlouho, dokud je nečinnosti zpracování provést. V rámci této smyčky vnořené smyčky opakovaně volání `PeekMessage`. Tak dlouho, dokud toto volání vrátí `CWinThread::PumpMessage` nenulovou hodnotu, smyčky volání provést normální překlad zpráv a odeslání. Přestože `PumpMessage` je nedokumentovaný, můžete prozkoumat jeho zdrojový kód v souboru ThrdCore.Cpp v adresáři \atlmfc\src\mfc instalace visual c++.

Jakmile vnitřní smyčka končí, vnější smyčka provádí nečinné `OnIdle`zpracování s jedním nebo více voláními . První výzva je pro účely knihovny MFC. Můžete provést další `OnIdle` volání, abyste mohli pracovat na pozadí.

Další informace o provádění nečinnosti zpracování naleznete v tématu [OnIdle](../mfc/reference/cwinthread-class.md#onidle) v knihovně knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny.

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)
