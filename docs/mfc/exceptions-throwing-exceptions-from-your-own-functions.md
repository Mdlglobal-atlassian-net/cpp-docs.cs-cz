---
title: 'Výjimky: Generování výjimek ve vašich vlastních funkcích'
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
ms.openlocfilehash: 030bf3db9ff305f35cbfb0b518c8704114ce083d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297941"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Výjimky: Generování výjimek ve vašich vlastních funkcích

Je možné používat výhradně pro zachytávaly výjimky vyvolané funkcí v knihovně MFC nebo jiných knihovnách paradigma zpracování výjimek knihovny MFC. Kromě zachytávání výjimek vyvolaných kód knihovny, může vyvolat výjimky z vlastního kódu při psaní funkcí, které se můžete setkat výjimečných podmínek.

Když je vyvolána výjimka, provedení aktuální funkce se zastaví a přejde přímo na **catch** bloku rámce vnitřní výjimka. Mechanismus výjimek obchází normální ukončení cestu z funkce. Musí být proto, že chcete odstranit tyto bloky paměti, které by se měla odstranit během normální ukončení.

#### <a name="to-throw-an-exception"></a>Chcete-li vyvolat výjimku

1. Použijte jednu z knihovny MFC pomocných funkcí, jako například `AfxThrowMemoryException`. Tyto funkce vyvolat objekt předběžně přidělené výjimky příslušného typu.

   Funkce v následujícím příkladu, pokusí se o přidělení dva bloky paměti a vyvolá výjimku, pokud se nezdaří buď přidělování:

   [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]

   Pokud první přidělení selže, může jednoduše vyvolat výjimky paměti. Pokud první přidělení je úspěšné, ale druhý se nezdaří, je nutné uvolnit první blok přidělení před vygenerováním výjimky. Pokud obě přidělení úspěšné, můžete normálně pokračovat a uvolnění bloky při ukončení funkce.

     - nebo –

1. Slouží k označení podmínku problém s výjimkou definovaný uživatelem. Položky libovolného typu, dokonce i celou třídu, můžete vyvolat jako výjimky.

   Následující příklad se pokusí zvukový signál prostřednictvím vlnové zařízení a vyvolá výjimku, pokud dojde k selhání.

   [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]

> [!NOTE]
>  Knihovny MFC výchozí zpracování výjimek, které se vztahuje pouze na ukazatele na `CException` objekty (a objekty `CException`-odvozené třídy). Výše uvedený příklad obchází mechanismus výjimek MFC.

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)
