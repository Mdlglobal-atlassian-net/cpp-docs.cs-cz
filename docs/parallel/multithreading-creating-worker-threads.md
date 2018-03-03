---
title: "Multithreading: Vytváření pracovních vláken | Microsoft Docs"
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
- multithreading [C++], worker threads
- background tasks [C++]
- threading [C++], worker threads
- worker threads [C++]
- threading [C++], creating threads
- threading [MFC], worker threads
- threading [C++], user input not required
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 94a047de82bebb03f681e1bfdf6f68d56554fe8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-creating-worker-threads"></a>Multithreading: Vytváření pracovních vláken
Pracovní podproces se často používá ke zpracování úlohy na pozadí, které uživatel by neměl mít čekat chcete pokračovat v používání aplikace. Úlohy, jako je při každém přepočítání a tisk na pozadí jsou dobrými příklady pracovních vláken. V tomto tématu najdete postup potřeba vytvořit pracovní vlákno. Témata zahrnují:  
  
-   [Spuštění vlákna](#_core_starting_the_thread)  
  
-   [Implementace řídící funkce](#_core_implementing_the_controlling_function)  
  
-   [Příklad](#_core_controlling_function_example)  
  
 Vytvoření pracovní vlákno je relativně jednoduché úlohy. Jsou zapotřebí pouze dva kroky pro spuštění vašeho vlákna: implementace řídící funkce a spuštění vlákna. Není nutné na odvození třídy z [CWinThread](../mfc/reference/cwinthread-class.md). Pokud budete potřebovat speciální verzi se můžete odvození třídy `CWinThread`, ale není nutné pro většinu jednoduchých pracovních vláken. Můžete použít `CWinThread` bez úprav.  
  
##  <a name="_core_starting_the_thread"></a>Spuštění vlákna  
 Existují dvě přetížené verze `AfxBeginThread`: ten, který lze vytvořit pouze pracovních vláken a jeden, který může vytvářet vlákna uživatelského rozhraní a pracovních vláken. Chcete-li zahájit provádění vašeho pracovního vlákna pomocí první přetížení, volejte [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), poskytuje následující informace:  
  
-   Adresa řídící funkce.  
  
-   Parametr, který má být předán řídící funkce.  
  
-   (Volitelné) Požadovaná priorita vlákna. Výchozí hodnota je s normální prioritou. Další informace o úrovních k dispozici s prioritou najdete v tématu [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
-   (Volitelné) Požadovaná velikost zásobníku pro vlákno. Výchozí hodnota je stejná velikost zásobníku jako vytváření vláken.  
  
-   (Volitelné) **CREATE_SUSPENDED** Pokud chcete, aby vlákno vytvořeno v pozastaveném stavu. Výchozí hodnota je 0 nebo normální spuštění vlákna.  
  
-   (Volitelné) Požadované zabezpečení atributy. Výchozí hodnota je stejný přístup jako nadřazené vlákno. Další informace o formátu informací zabezpečení najdete v tématu [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 `AfxBeginThread`vytvoří a inicializuje `CWinThread` objektu, se spustí a vrátí jeho adresu, takže můžete na něj odkazovat později. Kontroly se provádějí v celém procesu zajistit, že všechny objekty jsou deallocated správně má libovolná součást vytvoření selhat.  
  
##  <a name="_core_implementing_the_controlling_function"></a>Implementace řídící funkce  
 Řídící funkce definuje vlákno. Při zadání tato funkce se vlákna spustí a při jejím ukončení vlákno se ukončí. Tato funkce musí mít následující prototyp:  
  
```  
UINT MyControllingFunction( LPVOID pParam );  
```  
  
 Parametr je jediná hodnota. Hodnota, kterou obdrží funkce v tomto parametru je hodnota, která byla předána do konstruktoru při vytvoření objektu vlákna. Řídící funkce umí interpretovat tuto hodnotu jakýmkoli způsobem si zvolí. Mohou být považovány jako skalární hodnotu nebo ukazatel na strukturu obsahující několik parametrů, nebo můžete ignorovat. Pokud parametr odkazuje na strukturu, struktura slouží jenom k předání dat volající vlákno, ale taky k předávání dat zpět z vlákna volajícímu. Pokud používáte k předávání dat zpět na volající tato struktura, vlákno je potřeba volající až výsledky připravené oznámení. Informace o komunikaci z pracovního vlákna volajícímu najdete v tématu [Multithreading: tipy pro programování](../parallel/multithreading-programming-tips.md).  
  
 Když funkce skončí, měla by vrátit **Celé_číslo** hodnotu, která určuje důvod pro ukončení. Obvykle je tato ukončovací kód 0, čímž indikuje úspěšné provedení s jiné hodnoty, označující různých typů chyb. Toto je čistě závisí na implementaci. Některé vláken mohou udržovat počty využití objekty a vrátí aktuální počet použití tohoto objektu. Jak aplikace může načíst tuto hodnotu najdete v tématu [Multithreading: ukončení vláken](../parallel/multithreading-terminating-threads.md).  
  
 Existují některá omezení na co můžete dělat v vícevláknové programu napsané pomocí knihovny MFC. Popis těchto omezení a další tipy pro používání vláken najdete v tématu [Multithreading: tipy pro programování](../parallel/multithreading-programming-tips.md).  
  
##  <a name="_core_controlling_function_example"></a>Příklad řídící funkce  
 Následující příklad ukazuje, jak definovat řídící funkce a použít ho z jiného část programu.  
  
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
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Multithreading: Vytváření vláken uživatelského rozhraní](../parallel/multithreading-creating-user-interface-threads.md)  
  
## <a name="see-also"></a>Viz také  
 [Multithreading s použitím jazyka C++ a prostředí MFC](../parallel/multithreading-with-cpp-and-mfc.md)