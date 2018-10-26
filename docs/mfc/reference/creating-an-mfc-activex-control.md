---
title: Vytvoření ovládacího prvku ActiveX knihovny MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.activex.project
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68ad9b2627921024e5bd9477ee2aab62494b4912
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053068"
---
# <a name="creating-an-mfc-activex-control"></a>Vytvoření ovládacího prvku ActiveX knihovny MFC

Programy ovládacího prvku ActiveX jsou modulární programy určené k nadřazené aplikaci poskytnout konkrétní typ funkce. Můžete například vytvořit ovládacích prvcích jako tlačítko pro použití v dialogovém okně nebo nástrojů pro použití na webové stránce.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace najdete v tématu [ovládací prvky ActiveX](../activex-controls.md).

Nejjednodušší způsob, jak vytvořit ovládací prvek ActiveX knihovny MFC je použití [Průvodce ovládacím prvkem MFC ActiveX](../../mfc/reference/mfc-activex-control-wizard.md).

### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>Chcete-li vytvořit ovládací prvek ActiveX knihovny MFC pomocí Průvodce ovládacím prvkem MFC ActiveX

1. Postupujte podle pokynů v tématu nápovědy [vytvoření projektu pomocí Průvodce aplikací jazyka Visual C++](../../ide/creating-desktop-projects-by-using-application-wizards.md).

1. V **nový projekt** dialogové okno, vyberte **ovládací prvek ActiveX knihovny MFC** ikonu v podokně šablon a spusťte Průvodce pro ovládací prvek ActiveX knihovny MFC.

1. Definujte vaši [nastavení aplikace](../../mfc/reference/application-settings-mfc-activex-control-wizard.md), [názvy ovládacích prvků](../../mfc/reference/control-names-mfc-activex-control-wizard.md), a [řídit nastavení](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) pomocí Průvodce ovládacím prvkem ActiveX knihovny MFC.

    > [!NOTE]
    >  Přeskočení tohoto kroku zachová průvodce výchozí nastavení.

1. Klikněte na tlačítko **Dokončit** zavřete průvodce a otevření nového projektu ve vývojovém prostředí.

Po vytvoření projektu můžete zobrazit soubory vytvořené v **Průzkumníka řešení**. Další informace o souborech Průvodce vytvoří pro váš projekt, naleznete v generovaném souboru ReadMe.txt. Další informace o typech souborů naleznete v tématu [typy souborů vytvořené pro projekty Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md).

Po vytvoření projektu, průvodci kódem můžete přidat [funkce](../../ide/add-member-function-wizard.md), [proměnné](../../ide/add-member-variable-wizard.md), [události](../../ide/add-event-wizard.md), [vlastnosti](../../ide/names-add-property-wizard.md), a [metody](../../ide/add-method-wizard.md). Další informace o přizpůsobení ovládacího prvku ActiveX naleznete v tématu [ovládací prvky MFC ActiveX](../../mfc/mfc-activex-controls.md).

## <a name="see-also"></a>Viz také

[Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Stránky vlastností](../../ide/property-pages-visual-cpp.md)

