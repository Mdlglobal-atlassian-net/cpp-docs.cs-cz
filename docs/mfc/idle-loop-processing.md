---
title: Zpracování smyčky nečinnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0cad16ca383ebbcc3e24723443ab951b8c1f7ab0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429040"
---
# <a name="idle-loop-processing"></a>Zpracování smyčky nečinnosti

Mnoho aplikací provádění dlouhé zpracování "v pozadí." Někdy otázky výkonu při diktování pomocí multithreadingu pro takové činnosti. Vlákna zahrnují náklady na vývoj navíc, proto se nedoporučují pro jednoduché úlohy, jako je pracovní doba nečinnosti, který nemá MFC [OnIdle](../mfc/reference/cwinthread-class.md#onidle) funkce. Tento článek se zaměřuje na zpracování při nečinnosti. Další informace o multithreading, najdete v tématu [Témata multithreadingu](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Některé druhy zpracování na pozadí jsou odpovídajícím způsobem provést během intervalů, které uživatel nijak jinak v aplikaci. V aplikace vyvinutá pro operační systém Microsoft Windows aplikace může provádět zpracování doby nečinnosti rozdělením časově náročný proces na mnoha malých fragmenty. Po zpracování každého fragment, aplikace provede spuštění ovládacích prvků do Windows pomocí [PeekMessage](https://msdn.microsoft.com/library/windows/desktop/ms644943) smyčky.

Tento článek vysvětluje, dva způsoby, jak nečinnosti zpracování ve vaší aplikaci:

- Pomocí **PeekMessage** v knihovně MFC hlavní smyčka zpráv.

- Vkládání jiného **PeekMessage** smyčky někde jinde v aplikaci.

##  <a name="_core_peekmessage_in_the_mfc_message_loop"></a> PeekMessage ve smyčce zpráv knihovny MFC

V aplikace vyvinuté pomocí knihovny MFC, hlavní zprávy smyčky v `CWinThread` třída obsahuje smyčku, která volá [PeekMessage](https://msdn.microsoft.com/library/windows/desktop/ms644943) rozhraní API systému Win32. Smyčka také volání `OnIdle` členskou funkci `CWinThread` mezi zprávy. Aplikace může zpracovávat zprávy v této době nečinnosti tak, že přepíšete `OnIdle` funkce.

> [!NOTE]
>  `Run`, `OnIdle`, a některé další členské funkce jsou nyní členy třídy `CWinThread` , nikoli z třídy `CWinApp`. `CWinApp` je odvozen z `CWinThread`.

Další informace o provádění zpracování při nečinnosti, naleznete v tématu [OnIdle](../mfc/reference/cwinthread-class.md#onidle) v *odkaz knihovny MFC*.

##  <a name="_core_peekmessage_elsewhere_in_your_application"></a> PeekMessage jinde v aplikaci

Další metody pro provádění nečinnosti zpracování v aplikaci zahrnuje vložení smyčky zpráv v jednom z vašich funkcí. Tato smyčka zpráv je velmi podobný MFC hlavní smyčka zpráv, součástí [CWinThread::Run](../mfc/reference/cwinthread-class.md#run). To znamená, smyčky v MFC vyvinutou aplikaci, musíte provést řadu stejných funkcí, jako hlavní smyčka zpráv. Následující fragment kódu ukazuje vytvoření smyčky zpráv, který je kompatibilní s knihovnou MFC:

[!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]

Tento kód, vložený ve funkci, opakuje cyklus, jako je zpracování při nečinnosti provést. V rámci smyčky, vnořené smyčky opakovaně volá `PeekMessage`. Za předpokladu, že volání vrátí nenulovou hodnotu, volá smyčky `CWinThread::PumpMessage` provádět překlad normální zpráva a odesílání. I když `PumpMessage` nedokumentované, můžete zkontrolovat jeho zdrojový kód v souboru ThrdCore.Cpp v adresáři \atlmfc\src\mfc instalaci Visual C++.

Jednou konců vnitřní smyčku Vnější smyčka provádí zpracování při nečinnosti pomocí jednoho nebo více volání `OnIdle`. Pro účely knihovny MFC je první volání. Provedením dalšího volání `OnIdle` k provedení práce na pozadí.

Další informace o provádění zpracování při nečinnosti, naleznete v tématu [OnIdle](../mfc/reference/cwinthread-class.md#onidle) v odkazu knihovny MFC.

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)

