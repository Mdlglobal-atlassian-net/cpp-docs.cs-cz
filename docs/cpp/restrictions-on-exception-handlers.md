---
title: Omezení obslužných rutin výjimek
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 7d5bf20da61f4b9f5012b7f2aab932dfc904c302
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403357"
---
# <a name="restrictions-on-exception-handlers"></a>Omezení obslužných rutin výjimek

Hlavním omezením použití obslužných rutin výjimek v kódu je nemožnost použít **goto** příkazu Přejít do **__try** blok příkazů. Místo toho je nutné vstoupit do tohoto bloku příkazů prostřednictvím normálního toku řízení. Můžete přejít z celkového počtu **__try** příkaz blokovat a zanořovat obslužné rutiny výjimek dle libosti.

## <a name="see-also"></a>Viz také:

[Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)