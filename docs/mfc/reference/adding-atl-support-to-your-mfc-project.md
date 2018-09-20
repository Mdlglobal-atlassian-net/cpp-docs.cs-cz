---
title: Přidání podpory knihovny ATL do projektu knihovny MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.adding.atl.mfc
dev_langs:
- C++
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc0d21202478a02980dbc94dc866b769c3c71a9b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429731"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>Přidání podpory knihovny ATL do projektu knihovny MFC

Pokud jste již vytvořili aplikaci založené na knihovně MFC, pak můžete přidat podporu pro aktivní šablony knihovny (ATL) snadno spuštěním přidání podpory knihovny ATL pro Průvodce projektu knihovny MFC.

> [!NOTE]
>  ATL a MFC nejsou podporovány obecně v edicích Express sady Visual Studio.

> [!NOTE]
>  Tato podpora se vztahuje pouze na jednoduché objekty modelu COM, přidat do spustitelného souboru knihovny MFC ani do projektu knihovny DLL. Ostatní objekty modelu COM (včetně ovládacích prvků ActiveX) můžete přidat do projektů MFC, ale objekty nemusí fungovat podle očekávání.

### <a name="to-add-atl-support-to-your-mfc-project"></a>Chcete-li přidat podporu ATL do projektu knihovny MFC

1. V Průzkumníku řešení klikněte pravým tlačítkem na projekt, ke kterému chcete přidat podporu ATL.

1. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat třídu**.

1. Vyberte **přidat podporu ATL do projektu MFC** ikonu.

    > [!NOTE]
    >  Tato ikona se nachází ve složce ATL **kategorie** podokně.

1. Po zobrazení výzvy klikněte na tlačítko **Ano** přidat podporu ATL.

Další informace o způsobu přidání podpory knihovny ATL změn kódu projektu knihovny MFC naleznete v tématu [podrobnosti o podpoře knihovny ATL přidané Průvodcem knihovnou ATL](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)

## <a name="see-also"></a>Viz také

[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Přepisování virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Popisovače zpráv knihovny MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigace strukturou třídy](../../ide/navigating-the-class-structure-visual-cpp.md)
