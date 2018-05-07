---
title: 'Výjimky: Zkoumání obsahu výjimek | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7af858a7bd43bca2a04fac417c592f2dba979ffe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-examining-exception-contents"></a>Výjimky: Zkoumání obsahu výjimek
I když **catch** bloku argument může být téměř jakoukoli datového typu, funkce MFC throw výjimky typy odvozené od třídy `CException`. K zachycení výjimek vyvolané funkce MFC, potom napíšete **catch** bloku, jehož argumentem je ukazatel na `CException` objekt (nebo objekt odvozené od `CException`, například `CMemoryException`). V závislosti na přesné typ výjimky můžete zkontrolovat data členů objekt výjimky a shromažďovat informace o konkrétní příčina výjimky.  
  
 Například `CFileException` typ má `m_cause` datového člena, který obsahuje výčtový typ určující příčinou výjimky souboru. Některé příklady možné vrátit hodnoty jsou **CFileException::fileNotFound** a **CFileException::readOnly**.  
  
 Následující příklad ukazuje, jak zkontrolovat obsah `CFileException`. Jiné typy výjimka může být prověřen podobně.  
  
 [!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]  
  
 Další informace najdete v tématu [výjimky: uvolnění objektů ve výjimkách](../mfc/exceptions-freeing-objects-in-exceptions.md) a [výjimkami: zachycení a odstraňování výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

