---
title: 'Výjimky: Převádění z maker výjimek prostředí MFC'
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
ms.openlocfilehash: 59b83438d5341fd6a139af64a2f365a739438741
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394504"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Výjimky: Převádění z maker výjimek prostředí MFC

Toto je rozšířená.

Tento článek vysvětluje, jak převést existujícímu kódu napsanému s makry Microsoft Foundation Class – **zkuste**, **CATCH**, **THROW**, a tak dále, použít zpracování výjimek jazyka C++ klíčová slova **zkuste**, **catch**, a **throw**. Mezi témata patří:

- [Převod výhod](#_core_advantages_of_converting)

- [Převod kódu pomocí maker výjimek použití výjimek jazyka C++](#_core_doing_the_conversion)

##  <a name="_core_advantages_of_converting"></a> K výhodám tohoto převodu

Pravděpodobně není potřeba převést existující kód, i když byste měli znát rozdíly mezi implementací makra v MFC verze 3.0 a implementace v dřívějších verzích. Tyto rozdíly a následné změny v chování kódu jsou popsány v [výjimky: Změny maker pro výjimky ve verzi 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).

Hlavní výhody převodu jsou:

- Kód, který používá klíčová slova zpracování výjimek jazyka C++ kompiluje o něco menší. Soubor EXE nebo. KNIHOVNY DLL.

- C++ Klíčových slov zpracování výjimek jsou větší variabilitu: Jejich dokáže zpracovat výjimky libovolného datového typu, který je možné zkopírovat (**int**, **float**, **char**, a tak dále), kdežto makra zpracování výjimek pouze třídy `CException` třídy a z něj odvozenou.

Hlavní rozdíl mezi makra a klíčová slova je, že kód pomocí makra "automatické" odstraní zachycené výjimky, když výjimky dostane mimo rozsah. Kód pomocí klíčových slov není, takže musí explicitně odstranit zachycené výjimky. Další informace najdete v článku [výjimky: Zachytávání a mazání](../mfc/exceptions-catching-and-deleting-exceptions.md).

Další rozdíl je syntaxe. Syntaxe pro makra a klíčová slova se liší ve třech ohledech:

1. Argumenty a deklarace výjimek:

   A **CATCH** volání makra má následující syntaxi:

   **CATCH(** *exception_class*, *exception_object_pointer_name* **)**

   Všimněte si, že čárkami mezi název třídy a název objektu ukazatele.

   Výjimka deklarace **catch** – klíčové slovo používá tuto syntaxi:

   **catch(** *exception_type* *exception_name* **)**

   Příkazu deklarace. Tato výjimka označuje typ výjimky catch bloku obslužné rutiny.

2. Vymezení bloky catch:

   S makry **CATCH** – makro (s argumenty) začíná první blok catch; **AND_CATCH** – makro začne bloky následné catch a **END_CATCH** – makro Ukončí posloupnost bloky catch.

   S klíčovými slovy **catch** začíná každý blok catch – klíčové slovo (s deklarací výjimka). Neexistuje žádné protějškem **END_CATCH** – makro; catch bloku končí jeho pravou složenou závorku.

3. Výraz throw:

   Použití makra **THROW_LAST** pro opětovné vyvolání na aktuální výjimku. **Throw** – klíčové slovo se žádný argument má stejný účinek.

##  <a name="_core_doing_the_conversion"></a> Provádění převodu

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>Chcete-li převést kódu pomocí makra použití klíčových slov zpracování výjimek jazyka C++

1. Vyhledejte všechny výskyty makra MFC **zkuste**, **CATCH**, **AND_CATCH**, **END_CATCH**, **THROW**, a **THROW_LAST**.

2. Nahraďte nebo odstraňte všechny výskyty následující makra:

   **Zkuste** (nahraďte ho hodnotou **zkuste**)

   **ZACHYTIT** (nahraďte ho hodnotou **catch**)

   **AND_CATCH** (nahraďte ho hodnotou **catch**)

   **END_CATCH** (odstranit)

   **VYVOLAT** (nahraďte ho hodnotou **throw**)

   **THROW_LAST** (nahraďte ho hodnotou **throw**)

3. Upravte – makro argumentů tak, aby tvoří platný výjimka deklarace.

   Například změnit

   [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   až

   [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. Upravte kód v blocích catch tak, aby odstraní objekty výjimek podle potřeby. Další informace najdete v článku [výjimky: Zachytávání a mazání](../mfc/exceptions-catching-and-deleting-exceptions.md).

Tady je příklad použití maker výjimek prostředí MFC kód zpracování výjimek. Všimněte si, že protože kód v následujícím příkladu používá makra výjimku `e` se automaticky odstraní:

[!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

Kód v následujícím příkladu používá klíčová slova výjimek jazyka C++, výjimky se musí explicitně odstranit:

[!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

Další informace najdete v tématu [výjimky: Použití maker MFC a výjimek jazyka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)<br/>
