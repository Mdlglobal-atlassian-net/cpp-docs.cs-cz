---
title: 'TN032: Mechanismus výjimek MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.exceptions
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
ms.openlocfilehash: 210e47e117cd602ba77edd330205385f54199ce5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288750"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: Mechanismus výjimek MFC

Předchozí verze aplikace Visual C++ nepodporuje standardní mechanismu výjimek jazyka C++ a knihovna MFC poskytuje makra **TRY/CATCH a THROW** , které byly používány. Tato verze Visual C++ podporuje výjimky jazyka C++. Tato poznámka popsané některé podrobnosti implementace pokročilých předchozí makra včetně automaticky vyčištění zásobníku na základě objektů. Protože výjimky jazyka C++ podporuje ve výchozím nastavení uvolnění zásobníku, tato technická Poznámka už nejsou potřebná.

Odkazovat na [výjimky: Použití maker MFC a výjimek jazyka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) Další informace o rozdílech mezi v makrech MFC a nová klíčová slova jazyka C++.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
