---
title: "TN032: Mechanismus výjimek MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.exceptions
dev_langs: C++
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bf82d4b158cedd2d8f6916dfb01d26db6c62d83b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: mechanismus výjimek MFC
Předchozí verze aplikace Visual C++ nepodporuje standardní mechanismus výjimek C++ a MFC poskytuje makra **TRY/CATCH/THROW** použité místo. Tato verze aplikace Visual C++ plně podporuje výjimky jazyka C++. Tato poznámka zahrnutých některé pokročilé implementace podrobnosti o předchozí makra včetně postup automaticky čištění zásobníku na základě objektů. Vzhledem k tomu výjimky jazyka C++ podporují ve výchozím nastavení unwinding zásobníku, tato technická poznámka již není nezbytné.  
  
 Odkazovat na [výjimky: použití makrech MFC a výjimky jazyka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) Další informace o rozdílech mezi v makrech MFC a nové klíčová slova jazyka C++.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

