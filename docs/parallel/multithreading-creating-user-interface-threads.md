---
title: 'Multithreading: Vytváření vláken uživatelského rozhraní knihovny MFC'
ms.date: 08/27/2018
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
ms.openlocfilehash: 1cd28a848f9be223f43412c3e0f3961cef9db6c7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512085"
---
# <a name="multithreading-creating-mfc-user-interface-threads"></a>Multithreading: Vytváření vláken uživatelského rozhraní knihovny MFC

Vlákno uživatelského rozhraní se běžně používá ke zpracování vstupu uživatele a reakci na události uživatele nezávisle na vláknech spouštějících jiné části aplikace. Hlavní vlákno aplikace (poskytované v `CWinApp`odvozené třídě) již bylo vytvořeno a spuštěno. Toto téma popisuje kroky potřebné k vytvoření dalších vláken uživatelského rozhraní.

První věc, kterou je nutné provést při vytváření vlákna uživatelského rozhraní, je odvozena od třídy [CWinThread](../mfc/reference/cwinthread-class.md). Tuto třídu musíte deklarovat a implementovat pomocí maker [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) a [IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate) . Tato třída musí přepsat některé funkce a může přepsat jiné. Tyto funkce a co by měly být uvedeny v následující tabulce.

### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>Funkce, které se mají přepsat při vytváření vlákna uživatelského rozhraní

|Funkce|Účel|
|--------------|-------------|
|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)|Provede vyčištění při ukončení vlákna. Obvykle přepsáno.|
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)|Provede inicializaci instance vlákna. Musí být přepsáno.|
|[OnIdle –](../mfc/reference/cwinthread-class.md#onidle)|Provádí zpracování v nečinnosti specifické pro vlákno. Obvykle není přepsáno.|
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)|Filtrovat zprávy předtím, než jsou odesílány do `TranslateMessage` a `DispatchMessage`. Obvykle není přepsáno.|
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)|Zachytit neošetřené výjimky vyvolané obslužnými rutinami zpráv a příkazů vlákna. Obvykle není přepsáno.|
|[Spuštění](../mfc/reference/cwinthread-class.md#run)|Řídící funkce vlákna. Obsahuje čerpadlo zpráv. Zřídka přepsáno.|

Knihovna MFC poskytuje dvě verze funkce `AfxBeginThread` prostřednictvím přetížení parametru: jednu, která může pouze vytvořit pracovní vlákna, a jednu, která může vytvářet vlákna uživatelského rozhraní nebo pracovní vlákna. Chcete-li spustit vlákno uživatelského rozhraní, zavolejte druhé přetížení [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)a poskytněte následující informace:

- [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) třídy, ze `CWinThread`které jste odvozeni.

- Volitelné Požadovaná úroveň priority. Výchozí hodnota je normální priorita. Další informace o dostupných úrovních priority najdete v tématu [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) v Windows SDK.

- Volitelné Požadovaná velikost zásobníku pro vlákno. Výchozí hodnota je stejná velikost zásobníku jako při vytváření vlákna.

- Volitelné CREATE_SUSPENDED, pokud chcete, aby bylo vlákno vytvořeno v pozastaveném stavu. Výchozí hodnota je 0, nebo normální spuštění vlákna.

- Volitelné Požadované atributy zabezpečení Výchozí hodnota je stejný přístup jako u nadřazeného vlákna. Další informace o formátu těchto informací o zabezpečení najdete v tématu [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) v Windows SDK.

`AfxBeginThread`provede většinu práce za vás. Vytvoří nový objekt vaší třídy, inicializuje jej pomocí informací, které zadáte, a volání [CWinThread:: CreateThread](../mfc/reference/cwinthread-class.md#createthread) spustí spuštění vlákna. Kontroly jsou prováděny v rámci tohoto postupu, aby se zajistilo, že všechny objekty budou odstraněné správně, pokud nějaká část vytvoření selže.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Multithreading: Ukončování vláken](multithreading-terminating-threads.md)

- [Multithreading: Vytváření pracovních vláken](multithreading-creating-worker-threads.md)

- [Procesy a vlákna](/windows/win32/ProcThread/processes-and-threads)

## <a name="see-also"></a>Viz také:

[Multithreading s použitím jazyka C++ a prostředí MFC](multithreading-with-cpp-and-mfc.md)
