---
title: 'Výjimky: Změny maker pro výjimky ve verzi 3.0'
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: 82320b0c7ccd6766e016f0437633339f8f8f61d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365498"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Výjimky: Změny maker pro výjimky ve verzi 3.0

Toto je pokročilé téma.

Ve verzi mfc 3.0 a novějších byla makra zpracování výjimek změněna tak, aby používala výjimky jazyka C++. Tento článek popisuje, jak tyto změny mohou ovlivnit chování existujícího kódu, který používá makra.

Tento článek popisuje následující témata:

- [Typy výjimek a makro CATCH](#_core_exception_types_and_the_catch_macro)

- [Opětovné vyvolání výjimek](#_core_re.2d.throwing_exceptions)

## <a name="exception-types-and-the-catch-macro"></a><a name="_core_exception_types_and_the_catch_macro"></a>Typy výjimek a makro CATCH

V dřívějších verzích knihovny MFC makro **catch** používá informace typu za běhu knihovny MFC k určení typu výjimky; typ výjimky je určen, jinými slovy, na místě úlovku. S výjimkami jazyka C++ je však typ výjimky vždy určen na místě vyvolání typem objektu výjimky, který je vyvolán. To způsobí nekompatibility ve výjimečných případech, kdy se typ ukazatele na objekt throwd liší od typu objektu throwd.

Následující příklad ilustruje důsledek tohoto rozdílu mezi knihovnou MFC verze 3.0 a staršími verzemi:

[!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

Tento kód se chová odlišně ve verzi 3.0, protože ovládací prvek vždy předá první blok **catch** s odpovídající deklarací výjimky. Výsledek throw výraz

[!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

je hozen jako `CException*`, i když je `CCustomException`konstruován jako . Makro **CATCH** ve verzi knihovny MFC `CObject::IsKindOf` 2.5 a starších používá k testování typu za běhu. Vzhledem k tomu, že výraz

[!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

je true, první blok catch zachytí výjimku. Ve verzi 3.0, která používá výjimky jazyka C++ k implementaci mnoha maker pro `CException`zpracování výjimek, druhý blok catch odpovídá vyvolání .

Kód, jako je tento, je neobvyklý. Obvykle se zobrazí, když je objekt výjimky předán `CException*`jiné funkci, která přijímá obecné , provádí zpracování "pre-throw" a nakonec vyvolá výjimku.

Chcete-li tento problém vyřešit, přesuňte výraz throw z funkce do volajícího kódu a vyvolat výjimku skutečného typu známého kompilátoru v době, kdy je generována výjimka.

## <a name="re-throwing-exceptions"></a><a name="_core_re.2d.throwing_exceptions"></a>Opětovné vyvolání výjimek

Blok catch nemůže vyvolat stejný ukazatel výjimky, který byl zachycen.

Tento kód byl například platný v předchozích verzích, ale bude mít neočekávané výsledky s verzí 3.0:

[!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

Použití **THROW** v bloku catch `e` způsobí, že ukazatel bude odstraněn, takže vnější místo catch obdrží neplatný ukazatel. Použijte **THROW_LAST** k `e`opětovnému hodu .

Další informace naleznete v [tématu Výjimky: Zachycení a odstranění výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)
