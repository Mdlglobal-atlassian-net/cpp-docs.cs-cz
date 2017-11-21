---
title: "CString výjimka čištění | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 68fb6f60c46ff5094e1b7a578a47646f42cea79e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cstring-exception-cleanup"></a>CString výjimka čištění
V předchozích verzích MFC, je důležité, vyčistit [CString](../atl-mfc-shared/reference/cstringt-class.md) objekty po použití. MFC verze 3.0 a novějších explicitní čištění už není nezbytné.  
  
 V části výjimky C++ mechanismu, který MFC teď používá pro zpracování nemáte starat o čištění po výjimce. Popis toho, jak C++ "unwinds" zásobníku po výjimka zachycena, najdete v části [try, catch a throw – příkazy](../cpp/try-throw-and-catch-statements-cpp.md). I když používáte MFC **zkuste**/**CATCH** makra místo klíčová slova jazyka C++ **zkuste** a **catch**, MFC používá C++ mechanismus výjimek pod, takže stále není potřeba explicitně vyčistit.  
  
## <a name="see-also"></a>Viz také  
 [Řetězce (ATL a MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

