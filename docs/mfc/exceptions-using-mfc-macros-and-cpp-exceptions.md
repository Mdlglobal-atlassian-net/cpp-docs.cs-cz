---
title: 'Výjimky: Použití výjimek v makrech MFC a jazyce C++'
ms.date: 11/04/2016
helpviewer_keywords:
- exception objects [MFC]
- memory leaks [MFC], exception object not deleted
- exception handling [MFC], MFC
- try-catch exception handling [MFC], mixing MFC macros and C++ keywords
- exception objects [MFC], deleting
- exceptions [MFC], MFC macros vs. C++ keywords
- catch blocks [MFC], mixed
- exception handling [MFC], mixed-language
- nested try blocks [MFC]
- catch blocks [MFC], explicitly deleting code in
- try-catch exception handling [MFC], nested try blocks
- heap corruption [MFC]
- nested catch blocks [MFC]
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
ms.openlocfilehash: afad5335bedf001329ecb401a8a16c663afb5571
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371594"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Výjimky: Použití výjimek v makrech MFC a jazyce C++

Tento článek popisuje důležité informace pro psaní kódu, který používá makra zpracování výjimek knihovny MFC a klíčová slova pro zpracování výjimek jazyka C++.

Tento článek popisuje následující témata:

- [Míchání klíčových slov a maker výjimek](#_core_mixing_exception_keywords_and_macros)

- [Zkuste bloky uvnitř catch bloky](#_core_try_blocks_inside_catch_blocks)

## <a name="mixing-exception-keywords-and-macros"></a><a name="_core_mixing_exception_keywords_and_macros"></a>Míchání klíčových slov a maker výjimek

Makra výjimek knihovny MFC a klíčová slova výjimek jazyka C++ můžete kombinovat ve stejném programu. Makra knihovny MFC však nelze kombinovat s klíčovými slovy výjimky jazyka C++ ve stejném bloku, protože makra automaticky odstraňují objekty výjimek, když jsou mimo rozsah, zatímco kód používající klíčová slova pro zpracování výjimek nikoli. Další informace naleznete v článku [Výjimky: Zachycení a odstranění výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md).

Hlavní rozdíl mezi makry a klíčovými slovy spoáčy s toho, že makra "automaticky" odstraní zachycenou výjimku, když výjimka přejde mimo rozsah. Kód pomocí klíčových slov není; výjimky zachycené v bloku catch musí být explicitně odstraněny. Míchání maker a klíčových slov výjimky Jazyka C++ může způsobit nevracení paměti, pokud není odstraněn objekt výjimky, nebo poškození haldy při odstranění výjimky dvakrát.

Následující kód, například zruší platnost ukazatele výjimky:

[!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

K problému dochází, protože `e` je odstraněn při spuštění předá mimo "vnitřní" **CATCH** bloku. Použití **THROW_LAST** makra namísto příkazu **THROW** způsobí, že "vnější" **blok CATCH** obdrží platný ukazatel:

[!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

## <a name="try-blocks-inside-catch-blocks"></a><a name="_core_try_blocks_inside_catch_blocks"></a>Vyzkoušet bloky uvnitř catch bloků

Nelze znovu vyvolat aktuální výjimku z bloku **try,** který je uvnitř bloku **CATCH.** Následující příklad je neplatný:

[!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

Další informace naleznete v [tématu Exceptions: Examining Exception Contents](../mfc/exceptions-examining-exception-contents.md).

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)
