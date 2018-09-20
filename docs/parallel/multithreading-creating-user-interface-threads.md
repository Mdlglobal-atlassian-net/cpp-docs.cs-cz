---
title: 'Multithreading: Vytváření vláken uživatelského rozhraní MFC | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06158f50364320c96223d5627386a059761baa77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416315"
---
# <a name="multithreading-creating-mfc-user-interface-threads"></a>Multithreading: Vytváření vláken uživatelského rozhraní MFC

Vlákna uživatelského rozhraní se běžně používá pro zpracování vstupu uživatele a reagovat na události uživatele bez ohledu na jejich vláken v jiné části aplikace. Hlavního vlákna aplikace (podle vašeho `CWinApp`-odvozené třídy) je již vytvořena a spuštěna za vás. Toto téma popisuje kroky potřebné k vytvoření vlákna další uživatelského rozhraní.

První věc, kterou je třeba provést při vytváření vlákna uživatelského rozhraní je odvodit třídu z [CWinThread](../mfc/reference/cwinthread-class.md). Musíte deklarovat a implementovat tyto třídy pomocí [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) a [IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate) makra. Tato třída musí přepsat některé funkce a můžete přepsat ostatní. Tyto funkce a co by měl provádět jsou uvedené v následující tabulce.

### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>Funkce přepsat při vytváření vláken uživatelského rozhraní

|Funkce|Účel|
|--------------|-------------|
|[ExitInstance –](../mfc/reference/cwinthread-class.md#exitinstance)|Proveďte vyčištění při ukončení vlákna. Obvykle přepsána.|
|[InitInstance –](../mfc/reference/cwinthread-class.md#initinstance)|Provede inicializaci instance vlákna. Musí být přepsána.|
|[ONIDLE –](../mfc/reference/cwinthread-class.md#onidle)|Proveďte zpracování specifické pro vlákno doby nečinnosti. Obvykle není přepsána.|
|[PreTranslateMessage –](../mfc/reference/cwinthread-class.md#pretranslatemessage)|Filtrovat zprávy před odesláním do `TranslateMessage` a `DispatchMessage`. Obvykle není přepsána.|
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)|Zachytily neošetřené výjimky vyvolané obslužnými rutinami vlákna zpráv a příkazů. Obvykle není přepsána.|
|[Spuštění](../mfc/reference/cwinthread-class.md#run)|Řídící funkce pro vlákno. Obsahuje pumpu zpráv. Přepsat jen zřídka.|

Knihovna MFC poskytuje dvě verze funkce `AfxBeginThread` prostřednictvím přetížení parametru: jednu, která může pouze vytvořit pracovní vlákna, a jednu, která může vytvářet vlákna uživatelského rozhraní nebo pracovní vlákna. Chcete-li spustit vlákno uživatelského rozhraní, zavolejte druhé přetížení metody [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), zadejte následující informace:

- [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) třídy odvozené z `CWinThread`.

- (Volitelné) Požadovaná úroveň priority. Výchozí hodnota je normální priorita. Další informace o možných úrovních priority naleznete v tématu [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) v sadě Windows SDK.

- (Volitelné) Požadovaná velikost zásobníku pro vlákno. Výchozí hodnota je stejná velikost zásobníku jako u vytvářeného vlákna.

- (Volitelné) CREATE_SUSPENDED, pokud chcete, aby vlákno vytvořeno v pozastaveném stavu. Výchozí hodnota je 0 nebo normální spuštění vlákna.

- (Volitelné) Požadované atributy zabezpečení. Výchozí hodnota je stejný přístup jako k nadřazenému vláknu. Další informace o formátu bezpečnostních informací naleznete v tématu [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) v sadě Windows SDK.

`AfxBeginThread` Většina práce udělá za vás. Vytvoří nový objekt třídy, inicializuje ji s informacemi poskytujete a volání [CWinThread::CreateThread](../mfc/reference/cwinthread-class.md#createthread) která spustí provádění vlákna. Kontroly jsou prováděny v celém procesu zajistit, aby že všechny objekty jsou správně uvolněny by selhat některá část vytvoření.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Multithreading: Ukončení vláken](multithreading-terminating-threads.md)

- [Multithreading: Vytváření pracovních vláken](multithreading-creating-worker-threads.md)

- [Procesy a vlákna](/windows/desktop/ProcThread/processes-and-threads)

## <a name="see-also"></a>Viz také

[Multithreading s použitím jazyka C++ a prostředí MFC](multithreading-with-cpp-and-mfc.md)