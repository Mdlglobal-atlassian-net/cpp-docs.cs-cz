---
title: 'Multithreading: ukončení vláken v MFC'
ms.date: 08/27/2018
f1_keywords:
- CREATE_SUSPENDED
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
ms.openlocfilehash: db88f08a3eb9c219300e1359257706b44326d7ed
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140479"
---
# <a name="multithreading-terminating-threads-in-mfc"></a>Multithreading: ukončení vláken v MFC

Dvě běžné situace způsobují ukončení vlákna: řídicí funkce se ukončí nebo vlákno není povoleno, aby bylo možné provést dokončení. Pokud textový procesor použil vlákno pro tisk na pozadí, řídicí funkce by normálně ukončila, pokud byl tisk úspěšně dokončen. Pokud uživatel chce tisk zrušit, ale vlákno tisku na pozadí musí být předčasně ukončeno. Toto téma vysvětluje jak implementovat každou situaci a jak získat ukončovací kód vlákna po jeho ukončení.

- [Normální ukončení vlákna](#_core_normal_thread_termination)

- [Předčasné ukončení vlákna](#_core_premature_thread_termination)

- [Načítání ukončovacího kódu vlákna](#_core_retrieving_the_exit_code_of_a_thread)

## <a name="_core_normal_thread_termination"></a>Normální ukončení vlákna

V případě pracovního vlákna je normální ukončení vlákna jednoduché: Ukončete řídící funkci a vraťte hodnotu, která označuje důvod ukončení. Můžete použít buď funkci [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) , nebo příkaz **return** . Obvykle 0 znamená úspěšné dokončení, ale je to pro vás.

Pro vlákno uživatelského rozhraní je proces stejně jednoduchý: v rámci vlákna uživatelského rozhraní volejte [PostQuitMessage](/windows/win32/api/winuser/nf-winuser-postquitmessage) v Windows SDK. Jediným parametrem, který `PostQuitMessage` trvá, je ukončovací kód vlákna. Jako u pracovních vláken 0 obvykle znamená úspěšné dokončení.

## <a name="_core_premature_thread_termination"></a>Předčasné ukončení vlákna

Předčasné ukončení vlákna je skoro jednoduché: volejte [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) z vlákna. Předejte požadovaný ukončovací kód jako jediný parametr. Tím se zastaví provádění vlákna, zruší přidělení zásobníku vlákna, odpojí všechny knihovny DLL připojené k vláknu a odstraní objekt vlákna z paměti.

`AfxEndThread` musí být v rámci vlákna voláno, aby bylo ukončeno. Pokud chcete ukončit vlákno z jiného vlákna, je nutné nastavit metodu komunikace mezi dvěma vlákny.

## <a name="_core_retrieving_the_exit_code_of_a_thread"></a>Načítání ukončovacího kódu vlákna

Chcete-li získat ukončovací kód pracovního procesu nebo vlákna uživatelského rozhraní, zavolejte funkci [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread) . Informace o této funkci naleznete v Windows SDK. Tato funkce přebírá popisovač do vlákna (uložený v `m_hThread` datovém členu objektů `CWinThread`) a adresu DWORD.

Pokud je vlákno stále aktivní, `GetExitCodeThread` místo STILL_ACTIVE v zadané adrese DWORD; v opačném případě je ukončovací kód umístěn v této adrese.

Načítání ukončovacího kódu objektů [CWinThread](../mfc/reference/cwinthread-class.md) má další krok. Ve výchozím nastavení, když je ukončeno `CWinThread` vlákno, je objekt vlákna odstraněn. To znamená, že nebudete mít přístup k datovému členu `m_hThread`, protože objekt `CWinThread` už neexistuje. Chcete-li se této situaci vyhnout, proveďte jednu z následujících akcí:

- Nastavte datový člen `m_bAutoDelete` na hodnotu NEPRAVDA. To umožňuje, aby objekt `CWinThread` po ukončení vlákna držel. Poté, co bylo vlákno ukončeno, můžete přístup k datovému členu `m_hThread`. Pokud však použijete tento postup, zodpovídáte za zničení objektu `CWinThread`, protože ho nebude automaticky odstraňovat. Toto je upřednostňovaná metoda.

- Uložte popisovač vlákna samostatně. Po vytvoření vlákna zkopírujte jeho `m_hThread` datový člen (pomocí `::DuplicateHandle`) do jiné proměnné a přistoupit k němu přes tuto proměnnou. Tímto způsobem je objekt odstraněn automaticky, když dojde k ukončení, a stále můžete zjistit, proč bylo vlákno ukončeno. Dejte pozor, aby vlákno neukončilo před tím, než bude možné popisovač duplikovat. Nejbezpečnější způsob, jak to provést, je předat CREATE_SUSPENDED do [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), uložit popisovač a pak obnovit vlákno voláním [ResumeThread](../mfc/reference/cwinthread-class.md#resumethread).

Kterákoli z metod umožňuje určit, proč se objekt `CWinThread` ukončil.

## <a name="see-also"></a>Viz také

[Multithreading s použitím jazyka C++ a prostředí MFC](multithreading-with-cpp-and-mfc.md)<br/>
[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)<br/>
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[ExitThread –](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread)
