---
title: 'Multithreading: Ukončení vláken v prostředí MFC | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b192c0ee4bc7658fc39791545c4aa9334edd183
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131942"
---
# <a name="multithreading-terminating-threads-in-mfc"></a>Multithreading: Ukončení vláken v prostředí MFC
Dvě běžné situace způsobí ukončení vlákna: existuje řídící funkce nebo vláknu není povoleno dokončení. Pokud textový procesor používá vlákno pro tisk na pozadí, řídící funkce by jej měla ukončit normálně Pokud tisk úspěšně dokončen. Pokud chce uživatel zrušit tisk, ale vlákno tisku na pozadí musí být předčasně ukončeno. Toto téma vysvětluje, jak implementovat obě situace a jak získat ukončovací kód vlákna poté, co se jeho ukončení.  
  
- [Normální ukončení vlákna](#_core_normal_thread_termination)  
  
- [Předčasné ukončení vlákna](#_core_premature_thread_termination)  
  
- [Získání ukončovacího kódu vlákna](#_core_retrieving_the_exit_code_of_a_thread)  
  
##  <a name="_core_normal_thread_termination"></a> Normální ukončení vlákna  
 
U pracovního vlákna je normální ukončení vlákna jednoduché: Ukončí řídící funkci a vrátí hodnotu, která označuje důvod ukončení. Můžete použít buď [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) funkce nebo **vrátit** příkazu. Obvykle 0 znamená úspěšné dokončení, ale to je jenom na vás.  
  
Pro vlákno uživatelského rozhraní je proces stejně tak jednoduchý: prostřednictvím vlákna uživatelského rozhraní volejte [PostQuitMessage](http://msdn.microsoft.com/library/windows/desktop/ms644945) v sadě Windows SDK. Jediným parametrem, který `PostQuitMessage` přijímá, je ukončovací kód vlákna. Jako u pracovních vláken 0 obvykle znamená úspěšné dokončení.  
  
##  <a name="_core_premature_thread_termination"></a> Předčasné ukončení vlákna  
 
Předčasné ukončení vlákna je téměř stejně jednoduché: volání [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) z vlákna. Předejte požadovaný ukončovací kód jako jediný parametr. To zastaví provádění vlákna, zruší přidělení zásobníku vlákna, odpojí všechny k vláknu připojené DLL a odstraní objekt vlákna z paměti.  
  
`AfxEndThread` Musí být volána z v rámci vlákno ukončeno. Pokud chcete ukončit vlákno z jiného vlákna, musíte nastavit metodu komunikace mezi těmito dvěma vlákny.  
  
##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a> Získání ukončovacího kódu vlákna  
 
Chcete-li získat ukončovací kód pracovního procesu nebo vlákna uživatelského rozhraní, zavolejte [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190) funkce. Informace o této funkci najdete v tématu Windows SDK. Tato funkce přijímá zpracovávané vlákno (uložené v `m_hThread` datový člen `CWinThread` objekty) a adresu typu DWORD.  
  
Pokud je vlákno stále aktivní, `GetExitCodeThread` umístí STILL_ACTIVE zadaná adresa DWORD; v opačném případě ukončovací kód je umístěn v této adrese.  
  
Získání ukončovacího kódu z [CWinThread](../mfc/reference/cwinthread-class.md) objekty trvá přidat další krok. Ve výchozím nastavení když `CWinThread` vlákno ukončeno, objekt vlákna odstraněn. To znamená, že nemáte přístup `m_hThread` datový člen protože `CWinThread` objekt už existuje. Abyste předešli této situaci, proveďte jednu z následujících akcí:  
  
- Nastavte `m_bAutoDelete` datový člen na hodnotu FALSE. Díky tomu `CWinThread` objekt zachován poté, co je vlákno bylo ukončeno. Potom můžete přistupovat `m_hThread` datový člen po ukončení vlákna. Pokud použijete tento postup, ale budete muset pro zničení `CWinThread` objektu, protože rozhraní jej neodstraní automaticky za vás. Toto je upřednostňovaná metoda.  
  
- Store popisovač vlákna zvlášť. Potom, co je vlákno vytvořeno, zkopírujte jeho `m_hThread` datový člen (pomocí `::DuplicateHandle`) do jiné proměnné a přistupujte k němu prostřednictvím dané proměnné. Tímto způsobem bude objekt automaticky odstraněn, pokud dojde k ukončení a můžete stále zjistit, proč bylo vlákno ukončeno. Dbejte na to, že vlákno neskončilo dříve, než duplikujete popisovač. Nejbezpečnější způsob, jak to provést, je předat CREATE_SUSPENDED k [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), uložit popisovač a poté obnovit vlákno voláním [ResumeThread](../mfc/reference/cwinthread-class.md#resumethread).  
  
Některé z metod umožňuje zjistit, proč `CWinThread` byl ukončen objekt.  
  
## <a name="see-also"></a>Viz také  
 
[Multithreading s C++ a knihovnou MFC](multithreading-with-cpp-and-mfc.md)   
[_endthread _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)   
[_beginthread _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
[ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659)