---
title: "Výjimky: Uvolnění objektů ve výjimkách | Microsoft Docs"
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
- throwing exceptions [MFC], freeing objects in exceptions
- local exception handling
- memory leaks, caused by exception
- try-catch exception handling [MFC], destroying objects
- destroying objects [MFC]
- freeing objects [MFC]
- throwing exceptions [MFC], after destroying
- exception handling [MFC], destroying objects
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a422347e319fabbd91f20e0ebf7897865f1ca4c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Výjimky: Uvolnění objektů ve výjimkách
Tento článek vysvětluje potřeba a metodě uvolnění objektů, když dojde k výjimce. Témata zahrnují:  
  
-   [Zpracování výjimek místně](#_core_handling_the_exception_locally)  
  
-   [Vyvolání výjimek po zničení objektů](#_core_throwing_exceptions_after_destroying_objects)  
  
 Výjimky vydané pomocí rozhraní nebo pomocí vaší aplikace přerušení normálního toku programu. Proto je velmi důležité, abyste detailně sledovat objektů, takže můžete správně vyřazení je v případě, že je vyvolána výjimka.  
  
 Existují dvě primární metody k tomu.  
  
-   Zpracování výjimek místně pomocí **zkuste** a **catch** klíčová slova, pak odstraňte všechny objekty s jeden příkaz.  
  
-   Zrušení všech objektů v **catch** blok před způsobující výjimku mimo blok pro další zpracování.  
  
 Tyto dva přístupy jsou znázorněné dole jako řešení v následujícím příkladu problematické:  
  
 [!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]  
  
 Jak je uvedeno výše, `myPerson` nebudou odstraněna, pokud je vyvolána výjimka podle `SomeFunc`. Provádění přejde přímo na další vnější obslužná rutina výjimky, obcházení ukončení normální funkce a kód, který odstraní objekt. Ukazatele na objekt je mimo rozsah při výjimka ponechá funkce a paměti obsazené objekt se obnoví nikdy tak dlouho, dokud je aplikace spuštěna. Toto je nevrácená paměť systému; by být zjistil, že pomocí diagnostiky paměti.  
  
##  <a name="_core_handling_the_exception_locally"></a>Zpracování výjimek místně  
 **Try/catch –** zlepší poskytuje Obranným programovací metodu pro vyloučení nevracení paměti a zajištění, že jsou při výskytu výjimek zničen vašich objektů. Například z příkladu výše v tomto článku by mohla být přepsána následujícím způsobem:  
  
 [!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]  
  
 Tento nový příklad nastaví obslužnou rutinu výjimky pro zachycení výjimky a zacházejte s ním místně. Potom obvykle ukončí funkce a zničí objektu. Důležitým aspektem tohoto příkladu je, že se naváže kontext k zachycení výjimky **try/catch –** bloky. Bez lokálních výjimek rámečku by funkce nikdy vědět, že výjimku měl nebyly vytvořeny a nebude mít možnost ukončení normálně a odstraňte objekt.  
  
##  <a name="_core_throwing_exceptions_after_destroying_objects"></a>Vyvolání výjimek po zničení objektů  
 Dalším způsobem zpracování výjimek je je předat další vnější kontext zpracování výjimek. Ve vaší **catch** blok, můžete provést některé čištění místně přidělené objektů a poté vyvolat výjimku pro další zpracování.  
  
 Aktivační funkce může nebo nemusí být nutné se zrušit přidělení haldy objekty. Pokud funkci vždy zruší přidělení haldy objekt před vrácením v případě, že normální, potom funkce by také navrácení objektu haldy před způsobující výjimku. Na druhé straně Pokud funkce není navrátit normálně objekt před vrácením v případě, že normální, pak musíte se rozhodnout případ od případu zda objektu haldy by měl být navrácena.  
  
 Následující příklad ukazuje, jak místně přidělené objekty mohou být vyčištěna:  
  
 [!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]  
  
 Mechanismus výjimek automaticky zruší přidělení rámce objekty; je také označován destruktoru objektu rámce.  
  
 Při volání funkce, které můžete vyvolat výjimky, můžete použít **try/catch –** bloky catch výjimky a šance, že chcete odstranit všechny objekty, které jste vytvořili. Konkrétně Upozorňujeme, že mnoho funkcí MFC můžete vyvolat výjimky.  
  
 Další informace najdete v tématu [výjimkami: zachycení a odstraňování výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

