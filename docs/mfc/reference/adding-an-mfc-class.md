---
title: Přidání třídy knihovny MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.classes.adding.mfc
dev_langs:
- C++
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes
ms.assetid: 9a96b67f-40bf-43d4-8872-2f8dfc5404f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86e42ab5c2e8e15f5f56687b5ca99d160270017b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436361"
---
# <a name="adding-an-mfc-class"></a>Přidání třídy knihovny MFC

Chcete-li přidat třídy odvozené od třídy knihovny Microsoft Foundation Class (MFC) do svého projektu, použijte **přidat třídu** příkaz k dispozici v [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code). Zadejte název nové třídy, vyberte základní třídy a vyberte ID dialogových oken, ke kterému je přidružena (pokud existuje). Kód průvodce vytvoří soubor hlaviček a soubor implementace a přidá je do projektu.

> [!NOTE]
>  Třídy knihovny MFC lze přidat do aplikace knihovny ATL modelu COM, pokud jste původně [aplikace vytvořené pomocí podpory knihovny MFC](../../atl/reference/mfc-support-in-atl-projects.md). Můžete také přidat třídy knihovny MFC pro projekty Win32, které mají podporu knihovny MFC.

### <a name="to-add-an-mfc-class-to-your-project"></a>Přidání třídy knihovny MFC do projektu

1. Ze zobrazení tříd klikněte pravým tlačítkem na název projektu. Klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat třídu** otevřít [přidat třídu](../../ide/add-class-dialog-box.md) dialogové okno.

1. V podokně šablony vyberte **třídy knihovny MFC** a stiskněte klávesu **přidat** tlačítko.

1. Definovat nastavení pro novou třídu v [Průvodce třídami MFC](../../mfc/reference/mfc-add-class-wizard.md) dialogové okno.

1. Klikněte na tlačítko **Dokončit** zavřete průvodce a zobrazit novou třídu v zobrazení tříd. Můžete také zobrazit soubory vytvářené průvodcem v **Průzkumníka řešení**.

## <a name="see-also"></a>Viz také

[Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přehled tříd](../../mfc/class-library-overview.md)

