---
title: Vložení formuláře do projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83606041250dafed0ef57eb4eea18d7314e0bbef
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429263"
---
# <a name="inserting-a-form-into-a-project"></a>Vložení formuláře do projektu

Formuláře poskytují praktický kontejner pro ovládací prvky. Můžete snadno vložit formulář aplikace založené na knihovně MFC do vaší aplikace za předpokladu, že aplikace podporuje knihovny MFC.

### <a name="to-insert-a-form-into-your-project"></a>Vložení formuláře do projektu

1. Ze zobrazení tříd vyberte projekt, ke kterému chcete přidat formuláři a klikněte pravým tlačítkem myši.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat třídu**.

     Pokud **nový formulář** příkaz není k dispozici, váš projekt může být založen na aktivní šablony knihovny (ATL). Chcete-li přidat formuláře do projektu ATL, je třeba [určitá nastavení](../atl/reference/application-settings-atl-project-wizard.md) při prvním vytvoření projektu.

1. Z **MFC** složky, klikněte na tlačítko **třídy knihovny MFC**.

1. Pomocí Průvodce třídami MFC, ujistěte se, odvozovat nové třídy [CFormView](../mfc/reference/cformview-class.md).

Visual C++ přidá formuláře pro vaši aplikaci, otevřete v editoru dialogového okna tak, že můžete začít přidání ovládacích prvků a práce na jeho celkový návrh.

Můžete chtít provést následující kroky (není k dispozici pro aplikace založené na dialogu):

1. Přepsat `OnUpdate` členskou funkci.

1. Implementujte členskou funkci pro přesun dat z zobrazení do dokumentu.

1. Vytvoření `OnPrint` členskou funkci.

## <a name="see-also"></a>Viz také

[Zobrazení formulářů](../mfc/form-views-mfc.md)

