---
title: 'TN032: Mechanismus výjimek MFC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.exceptions
dev_langs:
- C++
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5256f787534ab408920f7154122ae0c5934019c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380838"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: mechanismus výjimek MFC
Předchozí verze aplikace Visual C++ nepodporuje standardní mechanismus výjimek C++ a MFC poskytuje makra **TRY/CATCH/THROW** použité místo. Tato verze aplikace Visual C++ plně podporuje výjimky jazyka C++. Tato poznámka zahrnutých některé pokročilé implementace podrobnosti o předchozí makra včetně postup automaticky čištění zásobníku na základě objektů. Vzhledem k tomu výjimky jazyka C++ podporují ve výchozím nastavení unwinding zásobníku, tato technická poznámka již není nezbytné.  
  
 Odkazovat na [výjimky: použití makrech MFC a výjimky jazyka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) Další informace o rozdílech mezi v makrech MFC a nové klíčová slova jazyka C++.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

