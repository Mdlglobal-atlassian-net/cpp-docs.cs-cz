---
title: 'TN032: Mechanismus výjimek MFC | Dokumentace Microsoftu'
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
ms.openlocfilehash: aee8ce02af874e1c3c30243a35e8f36acfce63f0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414755"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: mechanismus výjimek MFC

Předchozí verze aplikace Visual C++ nepodporuje standardní mechanismu výjimek jazyka C++ a knihovna MFC poskytuje makra **TRY/CATCH a THROW** , které byly používány. Tato verze Visual C++ podporuje výjimky jazyka C++. Tato poznámka popsané některé podrobnosti implementace pokročilých předchozí makra včetně automaticky vyčištění zásobníku na základě objektů. Protože výjimky jazyka C++ podporuje ve výchozím nastavení uvolnění zásobníku, tato technická Poznámka už nejsou potřebná.

Odkazovat na [výjimky: použití maker MFC a výjimek jazyka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) Další informace o rozdílech mezi v makrech MFC a nová klíčová slova jazyka C++.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

