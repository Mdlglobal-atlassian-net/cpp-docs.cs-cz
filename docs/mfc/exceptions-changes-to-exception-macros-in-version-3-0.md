---
title: 'Výjimky: Změny maker pro výjimky ve verzi 3.0 | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8829c018e51b81c0997092312e3e058d3086665b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417030"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Výjimky: Změny maker pro výjimky ve verzi 3.0

Toto je rozšířená.

Makra zpracování výjimek byly změněny v prostředí MFC verze 3.0 nebo novější, použití výjimek jazyka C++. Tento článek vysvětluje, jak tyto změny mohou ovlivnit chování existující kód, který používá makra.

Tento článek obsahuje následující témata:

- [Typy výjimek a CATCH – makro](#_core_exception_types_and_the_catch_macro)

- [Opětovné generování výjimek](#_core_re.2d.throwing_exceptions)

##  <a name="_core_exception_types_and_the_catch_macro"></a> Typy výjimek a CATCH – makro

V dřívějších verzích knihovny MFC **CATCH** – makro používá k určení typu výjimky MFC informace běhového typu; je určen typ výjimky, jinými slovy, v lokalitě catch. Výjimky jazyka C++ ale typ této výjimky je vždy určuje v lokalitě throw podle typu objektu výjimky, která je vyvolána. To způsobí nekompatibility ve výjimečných případech, kde se liší od typu k této výjimce dojde objektu typu ukazatel na objekt k této výjimce dojde.

Následující příklad ukazuje důsledkem tohoto rozdílu mezi MFC verze 3.0 a starší verze:

[!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

Tento kód se chová jinak než ve verzi 3.0 protože řízení se vždycky předá první **catch** blok s odpovídající deklaraci výjimky. Výsledek výraz throw

[!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

je vyvolána jako `CException*`, i když je vytvořena jako `CCustomException`. **CATCH** makra v MFC – verze 2.5 a starší používá `CObject::IsKindOf` otestovat typ v době běhu. Vzhledem k tomu, výraz

[!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

má hodnotu true, první blok catch zachytí výjimku. Ve verzi 3.0, která používá výjimky jazyka C++ k implementaci mnoha makra zpracování výjimek, odpovídá druhý bloku catch k této výjimce dojde `CException`.

Kód tímto způsobem neobvyklé. To se obvykle zobrazí, když výjimka objekt je předán do jiné funkce, která přijímá obecný `CException*`, provádí zpracování "před vyvolání výjimky" a nakonec vyvolává výjimku.

Chcete-li tento problém vyřešit, přesunout výraz throw z funkce do kódu volání a vyvolají výjimku skutečný typ pro kompilátor známým v době, kdy se vygeneruje výjimku.

##  <a name="_core_re.2d.throwing_exceptions"></a> Opětovné generování výjimek

Blok catch nejde aktivovat stejný ukazatel výjimka, která je zachycena.

Například tento kód byl platný v předchozích verzích ale budou mít neočekávané výsledky verze 3.0 od:

[!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

Pomocí **THROW** v catch blok způsobí, že ukazatel `e` odstranit, aby lokality vnější catch obdrží neplatný ukazatel. Použití **THROW_LAST** pro opětovné vyvolání `e`.

Další informace najdete v tématu [výjimky: výjimky zachycení a odstraňování](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

