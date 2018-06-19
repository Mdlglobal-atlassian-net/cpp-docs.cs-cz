---
title: 'Výjimky: Generování výjimek ve vašich vlastních funkcích | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dae6f2c0d1cab021cc91854a34f10423a1122dec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346191"
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

