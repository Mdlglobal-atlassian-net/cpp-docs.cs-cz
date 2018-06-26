---
title: 'Výjimky: Použití C++ výjimek v makrech MFC a | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 698d8a754716f6876f9a72a0d5043807a32d2089
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932205"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Výjimky: Použití výjimek v makrech MFC a jazyce C++
Tento článek popisuje důležité informace k zápisu kódu, který používá makra zpracování výjimek MFC i klíčová slova jazyka C++ zpracování výjimek.  
  
 Tento článek obsahuje následující témata:  
  
-   [Kombinace výjimek klíčová slova a makra](#_core_mixing_exception_keywords_and_macros)  
  
-   [Bloky try uvnitř catch – bloky](#_core_try_blocks_inside_catch_blocks)  
  
##  <a name="_core_mixing_exception_keywords_and_macros"></a> Kombinace výjimek klíčová slova a makra  
 Je možné kombinovat maker výjimek prostředí MFC a klíčových slov výjimka C++ ve stejné aplikaci. Ale MFC – makra nelze kombinovat s klíčovými slovy C++ výjimky v bloku stejné, protože makra odstranit objekty výjimek automaticky při jejich se dostala mimo rozsah, zatímco kódu pomocí zpracování výjimek klíčová slova nemá. Další informace najdete v článku [výjimkami: zachycení a odstraňování výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
 Hlavní rozdíl mezi makra a klíčová slova je, že makra "automatické" odstranit Zachycenou výjimku, když je výjimka mimo rozsah. Programování s využitím klíčová slova nemá; výjimky v bloku catch zachycené se musí explicitně odstranit. Kombinování makra a klíčová slova jazyka C++ výjimka může způsobit nevracení paměti, když není odstraněn objekt výjimky nebo poškození haldy výjimku při odstranění dvakrát.  
  
 Následující kód, například zruší platnost ukazatele výjimka:  
  
 [!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]  
  
 K problému dochází, protože `e` se odstraní při provádění předá mimo "vnitřní" **CATCH** bloku. Pomocí **throw_last –** makro místo **THROW** způsobí, že příkaz "vnější" **CATCH** bloku získat platný:  
  
 [!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]  
  
##  <a name="_core_try_blocks_inside_catch_blocks"></a> Try – bloky uvnitř bloků Catch  
 Nelze znovu vyvolání aktuální výjimku z uvnitř **zkuste** blok, který je uvnitř **CATCH** bloku. V následujícím příkladu je neplatný:  
  
 [!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]  
  
 Další informace najdete v tématu [výjimky: zkoumání obsahu výjimek](../mfc/exceptions-examining-exception-contents.md).  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

