---
title: 'TN032: mechanismus výjimek MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.exceptions
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
ms.openlocfilehash: f3f13bb40151d3b9ef0d57c7e769ca30fa629177
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633388"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: mechanismus výjimek MFC

Předchozí verze aplikace Visual C++ nepodporuje standardní mechanismu výjimek jazyka C++ a knihovna MFC poskytuje makra **TRY/CATCH a THROW** , které byly používány. Tato verze Visual C++ podporuje výjimky jazyka C++. Tato poznámka popsané některé podrobnosti implementace pokročilých předchozí makra včetně automaticky vyčištění zásobníku na základě objektů. Protože výjimky jazyka C++ podporuje ve výchozím nastavení uvolnění zásobníku, tato technická Poznámka už nejsou potřebná.

Odkazovat na [výjimky: použití maker MFC a výjimek jazyka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) Další informace o rozdílech mezi v makrech MFC a nová klíčová slova jazyka C++.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

