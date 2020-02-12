---
title: 'Multithreading: vytváření pracovních vláken v MFC'
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
ms.openlocfilehash: ab5b05b64ebcfbd6d15bd2229ee19d18fa7f919d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140517"
---
# <a name="multithreading-creating-worker-threads-in-mfc"></a>Multithreading: vytváření pracovních vláken v MFC

Pracovní vlákno se běžně používá ke zpracování úloh na pozadí, které by uživatel neměl čekat, než bude aplikace dál používat. Úkoly jako přepočítání a tisk na pozadí jsou dobrými příklady pracovních vláken. Toto téma podrobně popisuje kroky potřebné k vytvoření pracovního vlákna. Témata:

- [Spouští se vlákno.](#_core_starting_the_thread)

- [Implementace řídící funkce](#_core_implementing_the_controlling_function)

- [Příklad](#_core_controlling_function_example)

Vytvoření pracovního vlákna je poměrně jednoduchá úloha. K získání spuštěného vlákna jsou vyžadovány pouze dva kroky: implementace řídící funkce a spuštění vlákna. Není nutné odvozovat třídu z [CWinThread](../mfc/reference/cwinthread-class.md). Třídu můžete odvodit, pokud potřebujete speciální verzi `CWinThread`, ale není vyžadována pro většinu jednoduchých pracovních vláken. `CWinThread` můžete použít beze změny.

## <a name="_core_starting_the_thread"></a>Spouští se vlákno.

Existují dvě přetížené verze `AfxBeginThread`: jednu, která může vytvořit pouze pracovní vlákna a jednu, která může vytvořit jak vlákna uživatelského rozhraní, tak i pracovní vlákna. Chcete-li zahájit provádění pracovního vlákna pomocí prvního přetížení, zavolejte metodu [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)a poskytněte následující informace:

- Adresa řídící funkce.

- Parametr, který má být předán řídící funkci.

- Volitelné Požadovaná priorita vlákna. Výchozí hodnota je normální priorita. Další informace o dostupných úrovních priority najdete v tématu [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) v Windows SDK.

- Volitelné Požadovaná velikost zásobníku pro vlákno. Výchozí hodnota je stejná velikost zásobníku jako při vytváření vlákna.

- Volitelné CREATE_SUSPENDED, pokud chcete, aby bylo vlákno vytvořeno v pozastaveném stavu. Výchozí hodnota je 0, nebo normální spuštění vlákna.

- Volitelné Požadované atributy zabezpečení Výchozí hodnota je stejný přístup jako u nadřazeného vlákna. Další informace o formátu těchto informací o zabezpečení najdete v tématu [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) v Windows SDK.

`AfxBeginThread` vytvoří a inicializuje `CWinThread` objekt za vás, spustí ho a vrátí jeho adresu, abyste na něj mohli odkazovat později. Kontroly jsou prováděny v rámci tohoto postupu, aby se zajistilo, že všechny objekty budou odstraněné správně, pokud nějaká část vytvoření selže.

## <a name="_core_implementing_the_controlling_function"></a>Implementace řídící funkce

Řídicí funkce definuje vlákno. Při zadání této funkce se vlákno spustí a když se ukončí, vlákno se ukončí. Tato funkce by měla mít následující prototyp:

```cpp
UINT MyControllingFunction( LPVOID pParam );
```

Parametr je jediná hodnota. Hodnota, kterou funkce přijímá v tomto parametru, je hodnota, která byla předána konstruktoru při vytvoření objektu vlákna. Řídicí funkce může tuto hodnotu interpretovat jakýmkoli způsobem, který si zvolí. Může být zpracována jako skalární hodnota nebo ukazatel na strukturu obsahující více parametrů, nebo může být ignorována. Pokud parametr odkazuje na strukturu, struktura může být použita nejen k předání dat volajícímu vláknu, ale také k předání dat zpět z vlákna volajícímu. Použijete-li takovou strukturu k předání dat zpět volajícímu, vlákno musí předat volajícímu, když jsou výsledky připravené. Informace o komunikaci z pracovního vlákna k volajícímu naleznete v tématu [Multithreading: programovací tipy](multithreading-programming-tips.md).

Po ukončení funkce by měla vracet hodnotu UINT označující důvod ukončení. Obvykle je tento ukončovací kód 0 pro indikaci úspěšnosti s jinými hodnotami, které označují různé typy chyb. Toto je čistě závislá implementace. Některá vlákna můžou udržovat počty využití objektů a vracet aktuální počet použití daného objektu. Pokud chcete zjistit, jak můžou aplikace získat tuto hodnotu, přečtěte si téma [Multithreading: ukončení vláken](multithreading-terminating-threads.md).

Existují určitá omezení na to, co můžete dělat ve vícevláknovém programu napsaném pomocí knihovny MFC. Popis těchto omezení a dalších tipů k používání vláken naleznete v tématu [Multithreading: programovací tipy](multithreading-programming-tips.md).

## <a name="_core_controlling_function_example"></a>Příklad řídicí funkce

Následující příklad ukazuje, jak definovat řídící funkci a použít ji z jiné části programu.

```cpp
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

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Multithreading: Vytváření vláken uživatelského rozhraní](multithreading-creating-user-interface-threads.md)

## <a name="see-also"></a>Viz také

[Multithreading s použitím jazyka C++ a prostředí MFC](multithreading-with-cpp-and-mfc.md)
