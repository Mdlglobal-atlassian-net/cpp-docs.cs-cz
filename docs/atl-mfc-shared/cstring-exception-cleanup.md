---
title: CString – čištění výjimek
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
ms.openlocfilehash: d131ce8ebe5158d7f3a567580064068742b63707
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746224"
---
# <a name="cstring-exception-cleanup"></a>CString – čištění výjimek

V předchozích verzí knihovny MFC, je důležité Vyčistit [CString](../atl-mfc-shared/reference/cstringt-class.md) objekty po použití. S knihovnou MFC verze 3.0 nebo novější explicitní vyčištění už nejsou potřebná.

V části zpracování mechanismus, který se teď používá MFC výjimky jazyka C++ není nutné se starat o vyčištění po výjimce. Popis toho, jak C++ "unwinds" zásobníku po zachycení výjimky, přečtěte si téma [try, catch a throw – příkazy](../cpp/try-throw-and-catch-statements-cpp.md). I v případě, že budete používat knihovnu MFC **zkuste**/**CATCH** makra namísto klíčová slova jazyka C++ **zkuste** a **catch**, knihovna MFC používá jazyka C++ mechanismus výjimek pod, takže stále není nutné explicitně vyčistit.

## <a name="see-also"></a>Viz také:

[Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)
