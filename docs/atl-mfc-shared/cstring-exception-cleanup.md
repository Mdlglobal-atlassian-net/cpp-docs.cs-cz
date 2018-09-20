---
title: CString – čištění výjimek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81349135fa822627cb40bdcd2570276d8040e50e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385518"
---
# <a name="cstring-exception-cleanup"></a>CString – čištění výjimek

V předchozích verzí knihovny MFC, je důležité Vyčistit [CString](../atl-mfc-shared/reference/cstringt-class.md) objekty po použití. S knihovnou MFC verze 3.0 nebo novější explicitní vyčištění už nejsou potřebná.

V části zpracování mechanismus, který se teď používá MFC výjimky jazyka C++ není nutné se starat o vyčištění po výjimce. Popis toho, jak C++ "unwinds" zásobníku po zachycení výjimky, přečtěte si téma [try, catch a throw – příkazy](../cpp/try-throw-and-catch-statements-cpp.md). I v případě, že budete používat knihovnu MFC **zkuste**/**CATCH** makra namísto klíčová slova jazyka C++ **zkuste** a **catch**, knihovna MFC používá jazyka C++ mechanismus výjimek pod, takže stále není nutné explicitně vyčistit.

## <a name="see-also"></a>Viz také

[Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

