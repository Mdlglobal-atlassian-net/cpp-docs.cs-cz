---
title: Šablony dokumentů a proces vytvoření Document / View | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- icons, for multiple document templates
- document templates [MFC], and views
- document/view architecture [MFC], creating document/view
- single document template
- MFC, document templates
- multiple document template
- CDocTemplate class [MFC]
- templates [MFC], document templates
ms.assetid: 311ce4cd-fbdf-4ea1-a51b-5bb043abbcee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 182cf58b3ee712ef0d45719591e967c0b81909bd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426520"
---
# <a name="document-templates-and-the-documentview-creation-process"></a>Šablony dokumentů a proces tvorby v modelu dokument/zobrazení

Rozhraní pro správu složitého procesu vytváření dokumentů s jejich přidružené zobrazení a oken s rámečkem, používá dvě třídy šablony dokumentu: [csingledoctemplate –](../mfc/reference/csingledoctemplate-class.md) pro aplikace SDI a [cmultidoctemplate – ](../mfc/reference/cmultidoctemplate-class.md) pro aplikace MDI. A `CSingleDocTemplate` můžete vytvářet a ukládat dokumenty jednoho typu v čase. A `CMultiDocTemplate` udržuje seznam mnoho otevřených dokumentů jednoho typu.

Některé aplikace podporují více typů dokumentů. Aplikace může například podporovat dokumenty textu a grafiky dokumenty. V takové aplikace když uživatel vybere nový příkaz v nabídce Soubor dialogové okno zobrazuje seznam možných typů nový dokument otevřít. Pro každý typ podporovaného dokumentu aplikace používá objekt šablony odlišné dokumentu. Následující obrázek znázorňuje konfiguraci aplikace MDI, která podporuje dva typy dokumentu a ukazuje několik otevřené dokumenty.

![Aplikace MDI, která má dva typy dokumentu](../mfc/media/vc387h1.gif "vc387h1") aplikace MDI dva typy dokumentů

Šablony dokumentů jsou vytvářené a udržované pomocí objektu aplikace. Jeden z klíčů úlohy prováděné během vaší aplikace `InitInstance` funkce, je vytvořit jednu nebo více šablon dokumentů odpovídající typu. Tato funkce je popsána v [vytváření šablon dokumentů](../mfc/document-template-creation.md). Objekt aplikace ukládá ukazatel na každou šablonu dokumentu ve svém seznamu šablon a poskytuje rozhraní pro přidání šablony dokumentů.

Pokud budete potřebovat pro podporu dvou nebo více typů dokumentů, je nutné přidat další volání [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) pro každý typ dokumentu.

Ikona zaregistrován ke každé šabloně dokument podle jeho pozice v seznamu aplikace šablony dokumentů. Pořadí šablony dokumentů je určen podle pořadí, které jsou přidány pomocí volání `AddDocTemplate`. Knihovny MFC se předpokládá, že první ikona prostředků v aplikaci je ikona aplikace, další zdroj ikony je první ikona dokumentu a tak dále.

Šablona dokumentu je například třetí ze tří pro aplikaci. Pokud aplikace v indexu 3 existuje prostředek s ikonou, tato ikona se používá pro šablonu dokumentu. V opačném případě ikona na pozici 0 je použita jako výchozí.

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)<br/>
[Vytváření šablon dokumentů](../mfc/document-template-creation.md)<br/>
[Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md)<br/>
[Vztahy mezi objekty MFC](../mfc/relationships-among-mfc-objects.md)<br/>
[Vytváření nových dokumentů, oken a zobrazení](../mfc/creating-new-documents-windows-and-views.md)

