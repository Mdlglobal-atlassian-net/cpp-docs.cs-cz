---
title: Vytváření dokumentů rámce Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], creating
- document templates [MFC], and document frame windows
- windows [MFC], creating
- runtime, class information
- run-time class [MFC], and document frame window creation
- document frame windows [MFC], creating
- MFC, frame windows
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 172076113a6bd7e223d99c238d0e05987cdcaae6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433689"
---
# <a name="creating-document-frame-windows"></a>Vytváření oken s rámečkem v dokumentu

[Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md) ukazuje, jak [CDocTemplate](../mfc/reference/cdoctemplate-class.md) objekt orchestruje vytváření okna rámce, dokumentů a zobrazení a jejich připojením všechno dohromady. Tři [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) argumenty, které mají `CDocTemplate` konstruktor zadat okno rámce, dokumentů a zobrazení tříd, které šablony dokumentu vytvoří dynamicky v reakci na uživatelských příkazů jako je například nový příkaz na souboru nabídka nebo nové okno příkaz v nabídce okno MDI. Šablona dokumentu ukládá tyto informace pro pozdější použití při vytváření okna rámce pro zobrazení a dokumentu.

Pro [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) mechanismus fungovala správně, vaší odvozené třídy oken s rámečkem musí být deklarován s [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) – makro. Důvodem je, že rozhraní je potřeba vytvořit dokument pomocí mechanismu dynamické vytváření třídy oken s rámečkem `CObject`.

Když uživatel vybere příkaz, který vytvoří dokument, volá framework při dokumentu šablony k vytvoření objektu dokumentu, jeho zobrazení a okno rámce, který se zobrazí v zobrazení. Při vytváření okna rámce dokumentu, šablony dokumentu vytvoří objekt příslušné třídy – třída odvozená z [CFrameWnd](../mfc/reference/cframewnd-class.md) aplikace SDI nebo z [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) pro MDI aplikace. Rozhraní zavolá objekt okna rámce [loadframe –](../mfc/reference/cframewnd-class.md#loadframe) členská funkce, chcete-li získat informace o vytvoření z prostředků a k vytvoření okna Windows. Rozhraní framework připojí k objektu oken s rámečkem popisovač okna. Potom vytvoří zobrazení jako podřízeného okna okna rámce dokumentu.

Buďte opatrní při rozhodování, [když má být inicializováno](../mfc/when-to-initialize-cwnd-objects.md) vaše `CWnd`-odvozenému objektu.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Odvození třídy z objektu CObject (svůj mechanismus dynamické vytváření)](../mfc/deriving-a-class-from-cobject.md)

- [Vytváření dokumentů/zobrazení (šablony a vytvoření oken s rámečkem)](../mfc/document-view-creation.md)

- [Zničení oken s rámečkem](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>Viz také

[Použití oken s rámečkem](../mfc/using-frame-windows.md)

