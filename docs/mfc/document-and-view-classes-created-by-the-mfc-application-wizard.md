---
title: Dokumentů a zobrazení vytvořené průvodcem aplikací MFC tříd | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb1a1fc6c35bfb9589e827d798cb112640fa9b2f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417615"
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>Třídy dokumentů a zobrazení vytvořené průvodcem aplikací MFC

Průvodce aplikací MFC poskytuje výhodu na vašem programu vytvořením třídy základní dokumentů a zobrazení za vás. Pak můžete [mapování příkazů a zpráv pro tyto třídy](../mfc/reference/mapping-messages-to-functions.md) a použít editor zdrojového kódu jazyka Visual C++ pro zápis jejich členské funkce.

Třída dokumentu vytvořené průvodcem aplikací MFC je odvozená od třídy [CDocument](../mfc/reference/cdocument-class.md). Zobrazení třídy je odvozen z [CView](../mfc/reference/cview-class.md). Názvy, Průvodce aplikací poskytuje tyto třídy a soubory, které je obsahují jsou založeny na název projektu je zadat v dialogovém okně Průvodce aplikací. Stránka třídy generované v Průvodci aplikací slouží ke změně výchozích názvů.

Některé aplikace může potřebovat víc než jedna třída dokumentu, zobrazení třídy nebo třídy oken s rámečkem. Další informace najdete v tématu [více typů dokumentů, zobrazení a rámečku Windows](../mfc/multiple-document-types-views-and-frame-windows.md).

## <a name="see-also"></a>Viz také

[Document/View – architektura](../mfc/document-view-architecture.md)

