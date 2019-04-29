---
title: 'Multithreading: Ukončení vláken v prostředí MFC'
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
ms.openlocfilehash: dd11f5db646e172d7ea2c2cc646841249d95ef31
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407728"
---
# <a name="multithreading-terminating-threads-in-mfc"></a>Multithreading: Ukončení vláken v prostředí MFC

Dvě běžné situace způsobí ukončení vlákna: existuje řídící funkce nebo vláknu není povoleno dokončení. Pokud textový procesor používá vlákno pro tisk na pozadí, řídící funkce by jej měla ukončit normálně Pokud tisk úspěšně dokončen. Pokud chce uživatel zrušit tisk, ale vlákno tisku na pozadí musí být předčasně ukončeno. Toto téma vysvětluje, jak implementovat obě situace a jak získat ukončovací kód vlákna poté, co se jeho ukončení.

- [Normální ukončení vlákna](#_core_normal_thread_termination)

- [Předčasné ukončení vlákna](#_core_premature_thread_termination)

- [Získání ukončovacího kódu vlákna](#_core_retrieving_the_exit_code_of_a_thread)

##  <a name="_core_normal_thread_termination"></a> Normální ukončení vlákna

U pracovního vlákna je normální ukončení vlákna jednoduché: Ukončí řídící funkci a vrátí hodnotu, která označuje důvod ukončení. Můžete použít buď [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) funkce nebo **vrátit** příkazu. Obvykle 0 znamená úspěšné dokončení, ale to je jenom na vás.

Pro vlákno uživatelského rozhraní je proces stejně tak jednoduchý: prostřednictvím vlákna uživatelského rozhraní volejte [PostQuitMessage](/windows/desktop/api/winuser/nf-winuser-postquitmessage) v sadě Windows SDK. Jediným parametrem, který `PostQuitMessage` přijímá, je ukončovací kód vlákna. Jako u pracovních vláken 0 obvykle znamená úspěšné dokončení.

##  <a name="_core_premature_thread_termination"></a> Předčasné ukončení vlákna

Předčasné ukončení vlákna je téměř stejně jednoduché: Volání [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) z vlákna. Předejte požadovaný ukončovací kód jako jediný parametr. To zastaví provádění vlákna, zruší přidělení zásobníku vlákna, odpojí všechny k vláknu připojené DLL a odstraní objekt vlákna z paměti.

`AfxEndThread` Musí být volána z v rámci vlákno ukončeno. Pokud chcete ukončit vlákno z jiného vlákna, musíte nastavit metodu komunikace mezi těmito dvěma vlákny.

##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a> Získání ukončovacího kódu vlákna

Chcete-li získat ukončovací kód pracovního procesu nebo vlákna uživatelského rozhraní, zavolejte [GetExitCodeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodethread) funkce. Informace o této funkci najdete v tématu Windows SDK. Tato funkce přijímá zpracovávané vlákno (uložené v `m_hThread` datový člen `CWinThread` objekty) a adresu typu DWORD.

Pokud je vlákno stále aktivní, `GetExitCodeThread` umístí STILL_ACTIVE zadaná adresa DWORD; v opačném případě ukončovací kód je umístěn v této adrese.

Získání ukončovacího kódu z [CWinThread](../mfc/reference/cwinthread-class.md) objekty trvá přidat další krok. Ve výchozím nastavení když `CWinThread` vlákno ukončeno, objekt vlákna odstraněn. To znamená, že nemáte přístup `m_hThread` datový člen protože `CWinThread` objekt už existuje. Abyste předešli této situaci, proveďte jednu z následujících akcí:

- Nastavte `m_bAutoDelete` datový člen na hodnotu FALSE. Díky tomu `CWinThread` objekt zachován poté, co je vlákno bylo ukončeno. Potom můžete přistupovat `m_hThread` datový člen po ukončení vlákna. Pokud použijete tento postup, ale budete muset pro zničení `CWinThread` objektu, protože rozhraní jej neodstraní automaticky za vás. Toto je upřednostňovaná metoda.

- Store popisovač vlákna zvlášť. Potom, co je vlákno vytvořeno, zkopírujte jeho `m_hThread` datový člen (pomocí `::DuplicateHandle`) do jiné proměnné a přistupujte k němu prostřednictvím dané proměnné. Tímto způsobem bude objekt automaticky odstraněn, pokud dojde k ukončení a můžete stále zjistit, proč bylo vlákno ukončeno. Dbejte na to, že vlákno neskončilo dříve, než duplikujete popisovač. Nejbezpečnější způsob, jak to provést, je předat CREATE_SUSPENDED k [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), uložit popisovač a poté obnovit vlákno voláním [ResumeThread](../mfc/reference/cwinthread-class.md#resumethread).

Některé z metod umožňuje zjistit, proč `CWinThread` byl ukončen objekt.

## <a name="see-also"></a>Viz také:

[Multithreading s použitím jazyka C++ a prostředí MFC](multithreading-with-cpp-and-mfc.md)<br/>
[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)<br/>
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[ExitThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitthread)
