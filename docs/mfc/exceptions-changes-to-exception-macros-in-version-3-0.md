---
title: "Výjimky: Změny maker pro výjimky ve verzi 3.0 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 073715c72dfad83490b377b5d55e1169297be1ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Výjimky: Změny maker pro výjimky ve verzi 3.0
To je rozšířená.  
  
 V prostředí MFC verze 3.0 a novějších byly změněny makra zpracování výjimek používat výjimky jazyka C++. Tento článek vysvětluje, jak tyto změny mohou ovlivnit chování existující kód, který používá makra.  
  
 Tento článek obsahuje následující témata:  
  
-   [Typy výjimek a CATCH – makro](#_core_exception_types_and_the_catch_macro)  
  
-   [Znovu vyvolání výjimek](#_core_re.2d.throwing_exceptions)  
  
##  <a name="_core_exception_types_and_the_catch_macro"></a>Typy výjimek a CATCH – makro  
 V dřívějších verzích MFC **CATCH** makro použije k určení k výjimce typu MFC informace běhového typu; v výjimky typ je určen, jinými slovy, v lokalitě catch. S výjimky jazyka C++, ale v výjimky typ je vždy určen v lokalitě throw podle typu objektu výjimka, která je vyvolána výjimka. V případě výjimečných, kde typ má ukazatel na objekt výjimce dojde se liší od typ objektu výjimce dojde způsobí problémům s kompatibilitou.  
  
 Následující příklad ilustruje důsledků tento rozdíl mezi MFC verze 3.0 a starší verze:  
  
 [!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]  
  
 Tento kód se chová jinak ve verzi 3.0 protože ovládací prvek vždycky předá prvního **catch** blok s odpovídající deklarace výjimka. Výsledkem výrazu throw  
  
 [!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]  
  
 je vyvolána jako **CException\***, i když je sestavený jako **CCustomException**. **CATCH** makra v MFC – verze 2.5 a starší použije `CObject::IsKindOf` k testování typ za běhu. Protože výraz  
  
 [!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]  
  
 je nastavena hodnota true, první blok catch zachytí výjimky. Ve verzi 3.0, který používá výjimky jazyka C++ implementovat řadu makra zpracování výjimek, odpovídá vyvolané druhý blok catch `CException`.  
  
 Kód takto neobvyklé. Obvykle se zobrazuje při výjimce objekt předaný jinou funkci, která přijímá obecný **CException\***, provádí zpracování "předběžné throw" a nakonec vyvolá výjimku.  
  
 Chcete-li tento problém obejít, přesuňte výraz throw z funkce volání kódu a způsobí výjimku skutečný typ známé kompilátoru v době, kdy se vygeneruje výjimka.  
  
##  <a name="_core_re.2d.throwing_exceptions"></a>Znovu vyvolání výjimek  
 Blok catch nelze vyvolat stejné výjimky ukazatele, který ho zachycena.  
  
 Například tento kód platné v předchozích verzích, ale bude mít neočekávané výsledky s verze 3.0:  
  
 [!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]  
  
 Pomocí **THROW** ve catch bloku způsobí, že má ukazatel `e` odstranit, aby lokality vnější catch obdrží neplatný ukazatel. Použití `THROW_LAST` znovu vyvolat `e`.  
  
 Další informace najdete v tématu [výjimkami: zachycení a odstraňování výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

