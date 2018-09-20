---
title: 'Výjimky: Generování výjimek ve vašich vlastních funkcích | Dokumentace Microsoftu'
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
ms.openlocfilehash: a6ef86f54442031b4383e6a0b8cc6f57e4e53d58
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418421"
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

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

