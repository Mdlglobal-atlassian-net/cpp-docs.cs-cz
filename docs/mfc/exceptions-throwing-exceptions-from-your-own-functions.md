---
title: "Výjimky: Generování výjimek ve vašich vlastních funkcích | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15aeb1af7f41cf2df8be3f69657ec6870c55ab34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Výjimky: Generování výjimek ve vašich vlastních funkcích
Je možné použít zlepší zpracování výjimek MFC výhradně k zachycení výjimky vyvolané funkcí v MFC nebo jiné knihovny. Kromě zachytávání výjimek vyvolaných kódem knihovny, můžete vyvolat výjimky z vlastního kódu, pokud píšete funkce, které se můžete setkat výjimečných podmínek.  
  
 Pokud je vyvolána výjimka, provedení aktuální funkce se zastaví a přejde přímo na **catch** bloku rámce vnitřní výjimka. Mechanismus výjimek obchází normální výstupní cesta z funkce. Proto musí být nezapomeňte odstranit tyto bloky paměti, které by odstranil v normálním ukončení.  
  
#### <a name="to-throw-an-exception"></a>Chcete-li vyvolat výjimku  
  
1.  Použijte jednu z podpůrné funkce MFC, jako například `AfxThrowMemoryException`. Tyto funkce throw objekt předběžně přidělené výjimky příslušného typu.  
  
     V následujícím příkladu funkce pokusí přidělit dva bloky paměti a vyvolá výjimku, pokud se nezdaří buď přidělení:  
  
     [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]  
  
     Pokud první přidělení selže, můžete jednoduše vyvolat výjimku paměti. Pokud první přidělení je úspěšné, ale druhý se nezdaří, je nutné uvolnit první blok přidělení před způsobující výjimku. Pokud oba přidělení úspěšné, můžete pokračovat normálně a volné na bloky při ukončení funkce.  
  
     - nebo –  
  
2.  Uživatelem definované výjimka slouží k označení podmínku problém. Položku libovolného typu, celou skupinu, můžete vyvolat jako vaše výjimka.  
  
     V následujícím příkladu se pokusí prostřednictvím zařízení wave přehrát zvuk a vyvolá výjimku, pokud dojde k selhání.  
  
     [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]  
  
> [!NOTE]
>  Knihovny MFC výchozí ošetření výjimek se vztahuje pouze na ukazatele na `CException` objekty (a objekty `CException`-odvozené třídy). V předchozím příkladu obchází mechanismus výjimek MFC společnosti.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

