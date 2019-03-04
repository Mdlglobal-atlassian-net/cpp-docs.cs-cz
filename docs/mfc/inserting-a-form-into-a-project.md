---
title: Vložení formuláře do projektu
ms.date: 11/04/2016
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
ms.openlocfilehash: 2fa344f2d84b39be4ee36fd845edb82c14b6c519
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286527"
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

## <a name="see-also"></a>Viz také:

[Zobrazení formulářů](../mfc/form-views-mfc.md)
