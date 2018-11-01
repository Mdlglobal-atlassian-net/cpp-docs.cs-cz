---
title: 'Výjimky: Zkoumání obsahu výjimek'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
ms.openlocfilehash: 4355a575f29741d0c7b9f1e12e40ca9d977219b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630061"
---
# <a name="exceptions-examining-exception-contents"></a>Výjimky: Zkoumání obsahu výjimek

I když **catch** bloku argument může být prakticky libovolného datového typu, funkce MFC vyvolat výjimky, které typy odvozené od třídy `CException`. Zachytit výjimku vyvolána pomocí funkcí knihovny MFC, potom napíšete **catch** bloku, jehož argumentem je ukazatel na `CException` objektu (nebo objektu odvozené z `CException`, jako `CMemoryException`). V závislosti na přesné typ výjimky můžete prozkoumat datové členy objektu výjimky k získání informací o konkrétní příčina výjimky.

Například `CFileException` typ má `m_cause` datový člen, který obsahuje výčtový typ určující příčinu výjimku souborů. Příklady možných návratové hodnoty nejsou `CFileException::fileNotFound` a `CFileException::readOnly`.

Následující příklad ukazuje, jak zkontrolovat obsah `CFileException`. Podobně se dají prozkoumat další typy výjimek.

[!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]

Další informace najdete v tématu [výjimky: uvolnění objektů ve výjimkách](../mfc/exceptions-freeing-objects-in-exceptions.md) a [výjimky: výjimky zachycení a odstraňování](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

