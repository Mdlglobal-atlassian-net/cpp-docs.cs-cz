---
title: "Multithreading: Ukončení vláken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CREATE_SUSPENDED
dev_langs:
- C++
helpviewer_keywords:
- premature thread termination
- starting threads
- threading [MFC], terminating threads
- multithreading [C++], terminating threads
- threading [C++], stopping threads
- terminating threads
- stopping threads
- AfxEndThread method
ms.assetid: 4c0a8c6d-c02f-456d-bd02-0a8c8d006ecb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c287de62169ef5d205ac791071cee4b103f60abc
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2018
---
# <a name="multithreading-terminating-threads"></a>Multithreading: Ukončení vláken
Dvě běžné situace způsobí ukončení vlákna: řídící funkce nebo vlákno není povolené k zahájení dokončení. Pokud textový editor používá vlákno pro tisk na pozadí, řídící funkce by ukončit normálně, pokud tisk úspěšně dokončen. Pokud chce uživatel zrušit tisk, ale tisk vlákně na pozadí musí byla předčasně ukončena. Toto téma vysvětluje, jak implementovat každé situaci a jak získat kód ukončení vlákna po ukončí.  
  
-   [Normální ukončení vlákna](#_core_normal_thread_termination)  
  
-   [Předčasné ukončení vlákna](#_core_premature_thread_termination)  
  
-   [Načítání kód ukončení vlákna](#_core_retrieving_the_exit_code_of_a_thread)  
  
##  <a name="_core_normal_thread_termination"></a>Normální ukončení vlákna  
 Pracovní podproces normální ukončení vlákna je jednoduchý: Ukončete řídící funkce a vrátí hodnotu, která označuje, že důvod pro ukončení. Můžete použít buď [AfxEndThread –](../mfc/reference/application-information-and-management.md#afxendthread) funkce nebo `return` příkaz. Obvykle 0 znamená úspěšné dokončení, ale je to na vás.  
  
 Vlákna uživatelského rozhraní, tento proces je stejně jako prostý: z vlákna uživatelského rozhraní volejte [PostQuitMessage](http://msdn.microsoft.com/library/windows/desktop/ms644945) v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]. Parametr pouze který **PostQuitMessage** trvá je kód ukončení vlákna. Jako u pracovních vláken obvykle 0 znamená úspěšné dokončení.  
  
##  <a name="_core_premature_thread_termination"></a>Předčasné ukončení vlákna  
 Předčasné ukončení vlákna je téměř stejně jednoduché: volání [AfxEndThread –](../mfc/reference/application-information-and-management.md#afxendthread) z vlákna. Předejte požadovaný ukončovací kód jako jediný parametr. To zastaví provádění vlákna, zruší přidělení zásobníku podprocesu, odpojí všechny knihovny DLL, které jsou připojené k vlákno a odstraní objekt vlákna z paměti.  
  
 `AfxEndThread`musí být volat z vlákna ukončena. Pokud chcete ukončit vlákno z jiného vlákna, musíte nastavit metodu komunikace mezi dvěma vlákny.  
  
##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a>Načítání kód ukončení vlákna  
 Chcete-li získat ukončovací kód nebo vlákna uživatelského rozhraní, zavolejte [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190) funkce. Informace o této funkci najdete v tématu [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]. Tato funkce přebírá popisovač na vlákno (uložené v `m_hThread` data členem `CWinThread` objekty) a adresu `DWORD`.  
  
 Pokud je stále aktivní, vlákno **GetExitCodeThread** umístí **STILL_ACTIVE** v zadaných `DWORD` adresa; jinak, ukončovací kód je umístěn v tuto adresu.  
  
 Načítání ukončovací kód [CWinThread](../mfc/reference/cwinthread-class.md) objekty trvá na další krok. Ve výchozím nastavení když `CWinThread` ukončení vlákna, je odstraněn objekt přístup z více vláken. To znamená, že nelze získat přístup `m_hThread` – datový člen protože `CWinThread` objekt již existuje. Abyste předešli této situaci, proveďte jednu z následujících akcí:  
  
-   Nastavte `m_bAutoDelete` – datový člen k **FALSE**. To umožňuje `CWinThread` objekt zůstanou zachovány i po ukončení vlákno. Potom můžete přistupovat `m_hThread` – datový člen po ukončení vlákno. Pokud použijete tento postup, ale je zodpovědná za zničení `CWinThread` objekt, protože rozhraní nebude odstraní automaticky. Toto je upřednostňovaná metoda.  
  
-   Popisovač vlákna úložiště samostatně. Po vytvoření vlákno zkopírujte jeho `m_hThread` – datový člen (pomocí **:: DuplicateHandle**) do jiné proměnné a k němu přístup pomocí této proměnné. Tímto způsobem objekt je automaticky odstraněn, když dojde k ukončení a můžete stále zjistit, proč bylo vlákno ukončeno. Dávejte pozor, aby vlákno nezavře předtím, než můžete duplikovat popisovač. Nejbezpečnější způsob, jak to udělat, je předat **CREATE_SUSPENDED** k [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), uložte popisovač a poté obnovit vlákno voláním [ResumeThread](../mfc/reference/cwinthread-class.md#resumethread).  
  
 Buď metoda umožňuje určit, proč `CWinThread` objekt byl ukončen.  
  
## <a name="see-also"></a>Viz také  
 [Multithreading s použitím C++ a MFC](../parallel/multithreading-with-cpp-and-mfc.md)   
 [_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)   
 [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659)