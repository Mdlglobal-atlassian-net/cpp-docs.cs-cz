---
title: "Výjimky: Zkoumání obsahu výjimek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 953dd61247f7d14ad04d5d5f85529c89f3aaad9d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-examining-exception-contents"></a>Výjimky: Zkoumání obsahu výjimek
I když **catch** bloku argument může být téměř jakoukoli datového typu, funkce MFC throw výjimky typy odvozené od třídy `CException`. K zachycení výjimek vyvolané funkce MFC, potom napíšete **catch** bloku, jehož argumentem je ukazatel na `CException` objekt (nebo objekt odvozené od `CException`, například `CMemoryException`). V závislosti na přesné typ výjimky můžete zkontrolovat data členů objekt výjimky a shromažďovat informace o konkrétní příčina výjimky.  
  
 Například `CFileException` typ má `m_cause` datového člena, který obsahuje výčtový typ určující příčinou výjimky souboru. Některé příklady možné vrátit hodnoty jsou **CFileException::fileNotFound** a **CFileException::readOnly**.  
  
 Následující příklad ukazuje, jak zkontrolovat obsah `CFileException`. Jiné typy výjimka může být prověřen podobně.  
  
 [!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]  
  
 Další informace najdete v tématu [výjimky: uvolnění objektů ve výjimkách](../mfc/exceptions-freeing-objects-in-exceptions.md) a [výjimkami: zachycení a odstraňování výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

