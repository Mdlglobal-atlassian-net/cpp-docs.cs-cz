---
title: Vytváření šablon dokumentů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- document templates [MFC]
- constructors [MFC], document template
- document templates [MFC], creating
- MFC, document templates
- templates [MFC], document templates
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b1a9067929e96c6d3fd851168af079e7e825dcb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443629"
---
# <a name="document-template-creation"></a>Vytváření šablon dokumentů

Při vytváření nového dokumentu v reakci na **nový** nebo **otevřít** příkaz **souboru** nabídce dokumentu šablony také vytvoří nové okno rámce, pomocí kterého je možné zobrazit dokument.

Šablona dokumentu konstruktor Určuje typy dokumentů, oken a zobrazení, která bude moct vytvořit šablonu. Toto je určeno argumenty, které můžete předat do konstruktoru šablony dokumentu. Následující kód ukazuje vytvoření [cmultidoctemplate –](../mfc/reference/cmultidoctemplate-class.md) pro ukázkovou aplikaci:

[!code-cpp[NVC_MFCDocView#7](../mfc/codesnippet/cpp/document-template-creation_1.cpp)]

Ukazatel na novou `CMultiDocTemplate` objekt se používá jako argument [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate). Argumenty, které mají `CMultiDocTemplate` konstruktor obsahovat ID prostředku, které jsou spojené s nabídkami a akcelerátory typ dokumentu a tři použití [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) – makro. `RUNTIME_CLASS` Vrátí [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objekt třídy jazyka C++ s názvem jako svůj argument. Tři `CRuntimeClass` objektů předaných do konstruktoru šablony dokumentu zadejte informace potřebné k vytváření nových objektů zadané třídy během procesu vytváření dokumentu. Příklad ukazuje vytvoření šablonu dokumentu, která vytvoří `CScribDoc` objekty s `CScribView` objekty připojené. Zobrazení jsou orámovány standardní podřízených oken rámce MDI.

## <a name="see-also"></a>Viz také

[Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md)<br/>
[Vztahy mezi objekty MFC](../mfc/relationships-among-mfc-objects.md)<br/>
[Vytváření nových dokumentů, oken a zobrazení](../mfc/creating-new-documents-windows-and-views.md)

