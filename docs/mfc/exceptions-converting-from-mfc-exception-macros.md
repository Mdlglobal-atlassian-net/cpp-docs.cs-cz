---
title: 'Výjimky: Převádění z maker výjimek prostředí MFC'
ms.date: 08/27/2018
helpviewer_keywords:
- converting exceptions [MFC]
- exception objects [MFC]
- conversions [MFC], code written with MFC macros
- keywords [MFC], macros
- macrosv, C++ keywords
- exception objects [MFC], deleting
- CException class [MFC], deleting CException class objects
- exceptions [MFC], converting
- exceptions [MFC], deleting exception objects
- catch blocks [MFC], delimiting
- exception handling [MFC], converting exceptions
ms.assetid: bd3ac3b3-f3ce-4fdd-a168-a2cff13ed796
ms.openlocfilehash: 330f66b1f46542082637645ad53da016b434d4a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372019"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Výjimky: Převádění z maker výjimek prostředí MFC

Toto je pokročilé téma.

Tento článek vysvětluje, jak převést existující kód napsaný s makry třídy Microsoft Foundation – **TRY**, **CATCH**, **THROW**a tak dále – chcete-li použít klíčová slova c++ pro zpracování výjimek, **zkuste**, **catch**a **throw**. Témata:

- [Výhody konverze](#_core_advantages_of_converting)

- [Převod kódu s makry výjimek na použití výjimek jazyka C++](#_core_doing_the_conversion)

## <a name="advantages-of-converting"></a><a name="_core_advantages_of_converting"></a>Výhody konverze

Pravděpodobně není nutné převést existující kód, i když byste měli být vědomi rozdílů mezi implementacemi maker v knihovně MFC verze 3.0 a implementacemi v dřívějších verzích. Tyto rozdíly a následné změny v chování kódu jsou popsány v [exceptions: Změny makra výjimek ve verzi 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).

Hlavní výhody konverze jsou:

- Kód, který používá klíčová slova zpracování výjimek jazyka C++ zkompiluje na o něco menší . EXE nebo . Knihovny dll.

- Klíčová slova pro zpracování výjimek jazyka C++ jsou všestrannější: Mohou zpracovávat výjimky libovolného datového typu, který lze zkopírovat **(int**, **float**, **char**a tak dále), zatímco makra zpracovávají pouze výjimky třídy `CException` a tříd odvozené z ní.

Hlavní rozdíl mezi makry a klíčovými slovy spoje v tom, že kód používající makra "automaticky" odstraní zachycenou výjimku, když výjimka přejde mimo rozsah. Kód pomocí klíčových slov není, takže je nutné explicitně odstranit zachycenou výjimku. Další informace naleznete v článku [Výjimky: Zachycení a odstranění výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md).

Dalším rozdílem je syntaxe. Syntaxe maker a klíčových slov se liší ve třech ohledech:

1. Argumenty maker a deklarace výjimek:

   Vyvolání makra **CATCH** má následující syntaxi:

   **CATCH(** *exception_class*, *exception_object_pointer_name* **)**

   Všimněte si čárky mezi názvem třídy a názvem ukazatele objektu.

   Deklarace výjimky pro klíčové slovo **catch** používá tuto syntaxi:

   **úlovek(** *exception_type* *exception_name* **)**

   Tento příkaz deklarace výjimky označuje typ výjimky, kterou zpracovává blok catch.

2. Vymezení bloků úlovků:

   S makry **catch** makro (s jeho argumenty) začíná první catch bloku; **makro AND_CATCH** začíná následné bloky catch a **END_CATCH** makro ukončí posloupnost bloků catch.

   S klíčovými slovy catch **klíčové** slovo (s jeho deklarace výjimky) začíná každý blok catch. Makro **END_CATCH** neexistuje. blok catch končí jeho uzavírací závorkou.

3. Throw výraz:

   Makra používají **THROW_LAST** znovu vyvolat aktuální výjimku. Klíčové slovo **throw** bez argumentu má stejný účinek.

## <a name="doing-the-conversion"></a><a name="_core_doing_the_conversion"></a>Provedení převodu

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>Převod kódu pomocí maker pro použití klíčových slov pro zpracování výjimek jazyka C++

1. Vyhledejte všechny výskyty maker knihovny MFC **TRY**, **CATCH**, **AND_CATCH**, **END_CATCH**, **THROW**a **THROW_LAST**.

2. Nahraďte nebo odstraňte všechny výskyty následujících maker:

   **TRY** (Nahraďte jej **try)**

   **CATCH** (Nahraďte jej **úlovkem)**

   **AND_CATCH** (Nahraďte jej **úlovkem)**

   **END_CATCH** (Odstranit)

   **THROW** (Nahraďte jej **hodem)**

   **THROW_LAST** (Vyměňte jej **za hod)**

3. Upravte argumenty makra tak, aby tvořily platné deklarace výjimek.

   Například změna

   [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   na

   [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. Upravte kód v zachytávacích blocích tak, aby podle potřeby odstranil objekty výjimek. Další informace naleznete v článku [Výjimky: Zachycení a odstranění výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md).

Zde je příklad kódu pro zpracování výjimek pomocí makra výjimek knihovny MFC. Všimněte si, že vzhledem k tomu, `e` že kód v následujícím příkladu používá makra, výjimka je odstraněna automaticky:

[!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

Kód v následujícím příkladu používá klíčová slova výjimky Jazyka C++, takže výjimka musí být explicitně odstraněna:

[!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

Další informace naleznete v [tématu Exceptions: Using Makra knihovny MFC a C++ Exceptions](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)<br/>
