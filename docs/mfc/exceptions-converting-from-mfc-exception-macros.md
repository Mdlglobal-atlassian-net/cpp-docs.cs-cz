---
title: 'Výjimky: Převádění z maker výjimek prostředí MFC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8953cc28e35974f7a2a63754533ffd851ca62a3e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Výjimky: Převádění z maker výjimek prostředí MFC
To je rozšířená.  
  
 Tento článek vysvětluje, jak převést existující kód zapisovaný s makry Microsoft Foundation Class – **zkuste**, **CATCH**, **THROW**a tak dále – použít zpracování výjimek jazyka C++ klíčová slova **zkuste**, **catch**, a `throw`. Témata zahrnují:  
  
-   [Převod výhody](#_core_advantages_of_converting)  
  
-   [Převod kódu s použitím makra výjimek používat výjimky jazyka C++](#_core_doing_the_conversion)  
  
##  <a name="_core_advantages_of_converting"></a> Výhody převodu  
 Pravděpodobně není nutné převést stávající kód, i když byste měli znát rozdíly mezi implementací makra v MFC verze 3.0 a implementace v dřívějších verzích. Tyto rozdíly a následné změny v chování kódu jsou popsané v [výjimky: změny maker pro výjimky ve verzi 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).  
  
 Hlavní výhody převodu jsou:  
  
-   Kód, který používá klíčová slova jazyka zpracování výjimek C++ zkompiluje do mírně nižší. Soubor EXE nebo. KNIHOVNY DLL.  
  
-   Klíčová slova jazyka C++ zpracování výjimek jsou rozmanitější: můžete jejich zpracování výjimek datového typu, které lze kopírovat (`int`, **float**, `char`a tak dále), zatímco makra zpracování výjimek pouze třídy `CException` a třídy odvozené z něj.  
  
 Hlavní rozdíl mezi makra a klíčová slova je, že kód za použití makra "automatické" odstraní Zachycenou výjimku při výjimka mimo rozsah. Kódu pomocí klíčová slova neexistuje, takže musí explicitně odstranit Zachycenou výjimku. Další informace najdete v článku [výjimkami: zachycení a odstraňování výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
 Další rozdíl je syntaxe. Syntaxe makra a klíčová slova se liší v tři ohledech:  
  
1.  Argumenty a deklarace výjimka:  
  
     A **CATCH** makro volání má následující syntaxi:  
  
     **CATCH (** *exception_class*, *exception_object_pointer_name* **)**  
  
     Všimněte si, čárka název třídy a název objektu, který ukazatel.  
  
     Výjimka deklaraci pro **catch** – klíčové slovo používá tuto syntaxi:  
  
     **catch (** *exception_type* *exception_name ***)**  
  
     Tento příkaz deklarace výjimka označuje typ výjimky catch blokovat obslužné rutiny.  
  
2.  Vymezení bloků catch:  
  
     S makry **CATCH** – makro (s argumenty) začne první blok catch; `AND_CATCH` makro začne bloky catch následné a `END_CATCH` makro ukončí pořadí bloků catch.  
  
     S klíčovými slovy **catch** začne každého bloku catch – klíčové slovo (s jeho deklaraci výjimka). Neexistuje žádné protějškem `END_CATCH` makro; blokovat elementů end s jeho pravé složené závorce catch.  
  
3.  Throw výraz:  
  
     Použití makra `THROW_LAST` znovu vyvolat aktuální výjimku. `throw` – Klíčové slovo s žádný argument má stejný účinek.  
  
##  <a name="_core_doing_the_conversion"></a> Provádění převod  
  
#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>Chcete-li převést kódu pomocí makra používat klíčová slova, C++ zpracování výjimek  
  
1.  Vyhledejte všechny výskyty makry MFC **zkuste**, **CATCH**, `AND_CATCH`, `END_CATCH`, **THROW**, a `THROW_LAST`.  
  
2.  Nahraďte nebo odstranit všechny výskyty následující makra:  
  
     **Zkuste** (nahraďte ho **zkuste**)  
  
     **CATCH –** (nahraďte ho **catch**)  
  
     `AND_CATCH` (Nahraďte ho **catch**)  
  
     `END_CATCH` (Odstranit)  
  
     **THROW** (nahraďte ho `throw`)  
  
     `THROW_LAST` (Nahraďte ho `throw`)  
  
3.  Argumenty – makro upravte tak, aby tvoří platný výjimka deklarace.  
  
     Můžete například změnit  
  
     [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]  
  
     až  
  
     [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]  
  
4.  Upravte kód z bloků catch tak, aby odstraní objekty výjimek podle potřeby. Další informace najdete v článku [výjimkami: zachycení a odstraňování výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
 Tady je příklad kódu zpracování výjimek pomocí maker výjimek prostředí MFC. Všimněte si, že vzhledem k tomu, že kód v následujícím příkladu používá makra, výjimka `e` automaticky odstraněna:  
  
 [!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]  
  
 Kód v následujícím příkladu používá klíčová slova jazyka C++ výjimky, takže výjimka se musí explicitně odstranit:  
  
 [!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]  
  
 Další informace najdete v tématu [výjimky: použití makrech MFC a výjimky jazyka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

