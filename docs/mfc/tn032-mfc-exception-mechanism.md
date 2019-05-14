---
title: 'TN032: Mechanismus výjimek MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
ms.openlocfilehash: 5b419fdcc4f20579b1a809dd8a5cf6a93f4fe835
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611423"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: Mechanismus výjimek MFC

Předchozí verze aplikace Visual C++ nepodporuje standardní mechanismu výjimek jazyka C++ a knihovna MFC poskytuje makra **TRY/CATCH a THROW** , které byly používány. Tato verze Visual C++ podporuje výjimky jazyka C++. Tato poznámka popsané některé podrobnosti implementace pokročilých předchozí makra včetně automaticky vyčištění zásobníku na základě objektů. Protože výjimky jazyka C++ podporuje ve výchozím nastavení uvolnění zásobníku, tato technická Poznámka už nejsou potřebná.

Odkazovat na [výjimky: Použití maker MFC a výjimek jazyka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) Další informace o rozdílech mezi v makrech MFC a nová klíčová slova jazyka C++.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
