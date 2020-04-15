---
title: 'Výjimky: Generování výjimek ve vašich vlastních funkcích'
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
ms.openlocfilehash: 6484594df7636fd52ac46ab1cc212c8e2ec0278e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359280"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Výjimky: Generování výjimek ve vašich vlastních funkcích

Je možné použít paradigma zpracování výjimek knihovny MFC pouze k zachycení výjimek vyzdvižených funkcemi v knihovně MFC nebo jiných knihovnách. Kromě zachycení výjimky vyvolána kódu knihovny, můžete vyvolat výjimky z vlastního kódu, pokud píšete funkce, které mohou narazit na výjimečné podmínky.

Při vyvolání výjimky je zastaveno provádění aktuální funkce a přejde přímo do bloku **catch** nejvnitřnějšího rámce výjimky. Mechanismus výjimky obchází normální cestu ukončení z funkce. Proto je nutné odstranit bloky paměti, které by byly odstraněny v normálním ukončení.

#### <a name="to-throw-an-exception"></a>Vyvolání výjimky

1. Použijte jednu z pomocných funkcí `AfxThrowMemoryException`knihovny MFC, například . Tyto funkce vyvolat předpřípadě přidělené exception objekt příslušného typu.

   V následujícím příkladu se funkce pokusí přidělit dva bloky paměti a vyvolá výjimku, pokud se nezdaří přidělení:

   [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]

   Pokud se první přidělení nezdaří, můžete jednoduše vyvolat výjimku paměti. Pokud je první přidělení úspěšné, ale druhý selže, je nutné uvolnit první blok přidělení před vyvoláním výjimky. Pokud obě přidělení úspěšné, můžete pokračovat normálně a uvolnit bloky při ukončení funkce.

     - nebo -

1. K označení problémové podmínky použijte uživatelem definovanou výjimku. Jako výjimku můžete vyvolat položku libovolného typu, dokonce i celou třídu.

   Následující příklad se pokusí přehrát zvuk prostřednictvím zařízení wave a vyvolá výjimku, pokud dojde k selhání.

   [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]

> [!NOTE]
> Výchozí zpracování výjimek knihovny MFC platí pouze `CException` pro ukazatele `CException`na objekty (a objekty odvozených tříd). Výše uvedený příklad obchází mechanismus výjimek knihovny MFC.

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)
