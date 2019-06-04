---
title: 'Multithreading: Vytváření pracovních vláken v prostředí MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- multithreading [C++], worker threads
- background tasks [C++]
- threading [C++], worker threads
- worker threads [C++]
- threading [C++], creating threads
- threading [MFC], worker threads
- threading [C++], user input not required
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
ms.openlocfilehash: 38757337b1bfe5c7994f9a9f26aad2526aa0279c
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504582"
---
# <a name="multithreading-creating-worker-threads-in-mfc"></a>Multithreading: Vytváření pracovních vláken v prostředí MFC

Pracovní vlákno se běžně používá pro zpracování úloh na pozadí, které by neměl muset uživatel čekat pro pokračování v používání aplikace. Úlohy jako přepočet a tisk na pozadí jsou dobrým příkladem pracovních vláken. Toto téma podrobně popisuje kroky potřebné k vytvoření pracovního vlákna. Mezi témata patří:

- [Spuštění vlákna](#_core_starting_the_thread)

- [Implementace řídicí funkce](#_core_implementing_the_controlling_function)

- [Příklad](#_core_controlling_function_example)

Vytvoření pracovního vlákna je poměrně jednoduchá úloha. Pouze dva kroky jsou požadovány pro spuštění vašeho vlákna: implementace řídící funkce a spuštění vlákna. Není nutné odvozovat třídu z [CWinThread](../mfc/reference/cwinthread-class.md). Můžete třídu odvodit, pokud potřebujete speciální verzi `CWinThread`, ale není to vyžadováno pro většinu jednoduchých pracovních vláken. Můžete použít `CWinThread` beze změn.

##  <a name="_core_starting_the_thread"></a> Spuštění vlákna

Existují dvě přetížené verze `AfxBeginThread`: ten, který lze vytvořit pouze pracovní podprocesy a jedna, která může vytvářet vlákna uživatelského rozhraní a pracovních vláken. Chcete-li zahájit provádění vašeho pracovního vlákna pomocí prvního přetížení, zavolejte [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), zadejte následující informace:

- Adresa řídící funkce.

- Parametr, který má být předán řídicí funkci.

- (Volitelné) Požadovaná priorita vlákna. Výchozí hodnota je normální priorita. Další informace o možných úrovních priority naleznete v tématu [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) v sadě Windows SDK.

- (Volitelné) Požadovaná velikost zásobníku pro vlákno. Výchozí hodnota je stejná velikost zásobníku jako u vytvářeného vlákna.

- (Volitelné) CREATE_SUSPENDED, pokud chcete, aby vlákno vytvořeno v pozastaveném stavu. Výchozí hodnota je 0 nebo normální spuštění vlákna.

- (Volitelné) Požadované atributy zabezpečení. Výchozí hodnota je stejný přístup jako k nadřazenému vláknu. Další informace o formátu bezpečnostních informací naleznete v tématu [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) v sadě Windows SDK.

`AfxBeginThread` vytvoří a inicializuje `CWinThread` objektu, spustí jej a vrátí jeho adresu, takže na něj můžete později odkazovat. Kontroly jsou prováděny v celém procesu zajistit, aby že všechny objekty jsou správně uvolněny by selhat některá část vytvoření.

##  <a name="_core_implementing_the_controlling_function"></a> Implementace řídicí funkce

Řídicí funkce definuje vlákno. Při zadání této funkce se vlákno spustí a při jejím ukončení se vlákno ukončí. Tato funkce by měla mít následující prototyp:

```
UINT MyControllingFunction( LPVOID pParam );
```

Parametr je jednoduchá hodnota. Hodnota, kterou funkce přijímá v tomto parametru je hodnota, která byla předána konstruktoru při vytvoření objektu vlákna. Řídicí funkce může interpretovat tuto hodnotu, jakýmkoli způsobem si vybere. Lze považovat za skalární hodnotu nebo ukazatel na strukturu obsahující více parametrů, nebo se to dá ignorovat. Pokud parametr odkazuje na strukturu, struktura slouží pouze k předání dat od volajícího vláknu, ale také k předání dat z vlákna zpět volajícímu. Používáte-li takovouto strukturu k předání dat zpět volajícímu, musí vlákno oznámit volajícímu, že jsou výsledky připraveny. Informace o komunikaci z pracovního vlákna k volajícímu naleznete v tématu [Multithreading: Tipy pro programování](multithreading-programming-tips.md).

Když funkce skončí, měla by vrátit hodnotu UINT označující důvod ukončení. Obvykle je tento kód ukončení 0 označující úspěšné provedení s jinými hodnotami označení různých typů chyb. To se čistě závisí na konkrétní implementaci. Některá vlákna mohou udržovat počty využití objektů a vracet aktuální počet využití daného objektu. Jak můžou aplikace načíst tuto hodnotu najdete v tématu [Multithreading: Ukončení vláken](multithreading-terminating-threads.md).

Existují některá omezení, co můžete dělat ve vícevláknovém programu, vytvořeném pomocí knihovny MFC. Popisy těchto omezení a další tipy pro používání vláken naleznete v tématu [Multithreading: Tipy pro programování](multithreading-programming-tips.md).

##  <a name="_core_controlling_function_example"></a> Příklad řídicí funkce

Následující příklad ukazuje, jak definovat řídicí funkci a použít ji z jiné části programu.

```
UINT MyThreadProc( LPVOID pParam )
{
    CMyObject* pObject = (CMyObject*)pParam;

    if (pObject == NULL ||
        !pObject->IsKindOf(RUNTIME_CLASS(CMyObject)))
    return 1;   // if pObject is not valid

    // do something with 'pObject'

    return 0;   // thread completed successfully
}

// inside a different function in the program
.
.
.
pNewObject = new CMyObject;
AfxBeginThread(MyThreadProc, pNewObject);
.
.
.
```

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Multithreading: Vytváření vláken uživatelského rozhraní](multithreading-creating-user-interface-threads.md)

## <a name="see-also"></a>Viz také:

[Multithreading s použitím jazyka C++ a prostředí MFC](multithreading-with-cpp-and-mfc.md)
