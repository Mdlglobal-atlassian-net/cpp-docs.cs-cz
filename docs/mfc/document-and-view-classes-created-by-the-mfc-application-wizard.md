---
title: Třídy dokumentů a zobrazení vytvořené průvodcem aplikací MFC
ms.date: 11/04/2016
helpviewer_keywords:
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
ms.openlocfilehash: 95b50e34d612c3b8f5dea2f8b469bd6c65182d41
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271447"
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>Třídy dokumentů a zobrazení vytvořené průvodcem aplikací MFC

Průvodce aplikací MFC poskytuje výhodu na vašem programu vytvořením třídy základní dokumentů a zobrazení za vás. Pak můžete [mapování příkazů a zpráv pro tyto třídy](../mfc/reference/mapping-messages-to-functions.md) a použít editor zdrojového kódu jazyka Visual C++ pro zápis jejich členské funkce.

Třída dokumentu vytvořené průvodcem aplikací MFC je odvozená od třídy [CDocument](../mfc/reference/cdocument-class.md). Zobrazení třídy je odvozen z [CView](../mfc/reference/cview-class.md). Názvy, Průvodce aplikací poskytuje tyto třídy a soubory, které je obsahují jsou založeny na název projektu je zadat v dialogovém okně Průvodce aplikací. Stránka třídy generované v Průvodci aplikací slouží ke změně výchozích názvů.

Některé aplikace může potřebovat víc než jedna třída dokumentu, zobrazení třídy nebo třídy oken s rámečkem. Další informace najdete v tématu [více typů dokumentů, zobrazení a rámečku Windows](../mfc/multiple-document-types-views-and-frame-windows.md).

## <a name="see-also"></a>Viz také:

[Document/View – architektura](../mfc/document-view-architecture.md)
