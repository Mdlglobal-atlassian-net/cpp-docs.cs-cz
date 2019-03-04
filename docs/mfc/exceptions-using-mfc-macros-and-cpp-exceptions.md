---
title: 'Výjimky: Použití maker MFC a výjimek jazyka C++'
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
ms.openlocfilehash: 00e88ddabf3a8e8b591bebae7ebc8ced0e1dc637
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297707"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Výjimky: Použití maker MFC a výjimek jazyka C++

Tento článek popisuje důležité informace k zápisu kódu, který používá makra zpracování výjimek knihovny MFC a klíčových slov zpracování výjimek jazyka C++.

Tento článek obsahuje následující témata:

- [Kombinování klíčová slova výjimek a makra](#_core_mixing_exception_keywords_and_macros)

- [Bloky try dovnitř bloky catch](#_core_try_blocks_inside_catch_blocks)

##  <a name="_core_mixing_exception_keywords_and_macros"></a> Kombinování klíčová slova výjimek a makra

Můžete kombinovat maker výjimek prostředí MFC a klíčová slova výjimek jazyka C++ ve stejném programu. Nemůžete ale kombinovat maker knihovny MFC s klíčová slova výjimek jazyka C++ ve stejném bloku protože makra objektů výjimek automaticky odstranit při mizení z rozsahu, zatímco kód pomocí klíčových slov zpracování výjimek ne. Další informace najdete v článku [výjimky: Zachytávání a mazání](../mfc/exceptions-catching-and-deleting-exceptions.md).

Hlavní rozdíl mezi makra a klíčová slova je, že makra "automatické" odstranit zachycené výjimky, když výjimky dostane mimo rozsah. Kód pomocí klíčových slov není; výjimky zachyceny v bloku catch se musí explicitně odstranit. Kombinování maker a klíčová slova výjimek jazyka C++ může způsobit nevracení paměti při objektu výjimky není odstranění nebo poškození haldy výjimku při odstranění dvakrát.

Následující kód například zruší platnost ukazatel výjimka:

[!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

K problému dochází, protože `e` se odstraní, když je spuštění úspěšné mimo "vnitřní" **CATCH** bloku. Pomocí **THROW_LAST** – makro místo **THROW** způsobí, že příkaz "vnější" **CATCH** bloku získat platný ukazatel:

[!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

##  <a name="_core_try_blocks_inside_catch_blocks"></a> Uvnitř bloků Catch bloky try

Nelze znovu vyvolat na aktuální výjimku v rámci **zkuste** blok, který se nachází uvnitř **CATCH** bloku. V následujícím příkladu je neplatný:

[!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

Další informace najdete v tématu [výjimky: Zkoumání obsahu výjimek](../mfc/exceptions-examining-exception-contents.md).

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)
