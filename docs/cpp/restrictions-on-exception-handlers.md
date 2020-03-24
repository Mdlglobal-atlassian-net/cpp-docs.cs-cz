---
title: Omezení obslužných rutin výjimek
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 54bf4a44d06eacd22dc4b9819d160d3c6a66c684
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179078"
---
# <a name="restrictions-on-exception-handlers"></a>Omezení obslužných rutin výjimek

Hlavním omezením pro použití obslužných rutin výjimek v kódu je, že nelze použít příkaz **goto** pro přechod do bloku příkazu **__try** . Místo toho je nutné vstoupit do tohoto bloku příkazů prostřednictvím normálního toku řízení. Můžete přejít ven z bloku příkazu **__try** a vnořovat obslužné rutiny výjimek, jak zvolíte.

## <a name="see-also"></a>Viz také

[Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
