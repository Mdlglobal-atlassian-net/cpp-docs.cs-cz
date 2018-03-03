---
title: "Vytváření šablon dokumentů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- document templates [MFC]
- constructors [MFC], document template
- document templates [MFC], creating
- MFC, document templates
- templates [MFC], document templates
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 04950601a74b1ed3e44b236e1d07dcdff997eca6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="document-template-creation"></a>Vytváření šablon dokumentů
Při vytváření nového dokumentu v reakci na `New` nebo **otevřete** příkaz **souboru** nabídce Šablona dokumentu také vytvoří nové okně s rámečkem prostřednictvím pro zobrazení dokumentu.  
  
 Konstruktor šablony dokumentu určuje, jaké typy dokumentů, oken a zobrazení, bude možné vytvořit šablonu. To je dáno argumenty, které můžete předat do konstruktoru šablony dokumentu. Následující kód ukazuje vytvoření [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) pro ukázkovou aplikaci:  
  
 [!code-cpp[NVC_MFCDocView#7](../mfc/codesnippet/cpp/document-template-creation_1.cpp)]  
  
 Ukazatel na novou `CMultiDocTemplate` objekt se používá jako argument pro [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate). Argumenty, které mají `CMultiDocTemplate` konstruktor zahrnují ID prostředku přidružené nabídek a akcelerátorů typ dokumentu a tři používání [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) makro. `RUNTIME_CLASS`Vrátí [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objekt pro C++ třída s názvem jako její argument. Tří `CRuntimeClass` objekty předaný konstruktoru šablony dokumentu zadejte informace potřebné k vytváření nových objektů třídy zadaný během procesu vytváření dokumentu. Tento příklad ukazuje vytvoření šablony dokumentu, který vytváří `CScribDoc` objekty s `CScribView` objekty, které jsou připojené. Zobrazení jsou rámcová ve standardní MDI podřízená rámce okna.  
  
## <a name="see-also"></a>Viz také  
 [Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md)   
 [Vztahy mezi objekty MFC](../mfc/relationships-among-mfc-objects.md)   
 [Vytváření nových dokumentů, oken a zobrazení](../mfc/creating-new-documents-windows-and-views.md)

