---
title: Přidání třídy knihovny MFC z knihovny typů
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: e8264de2c717c874da157cb29ad5e336e3ecbd0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296745"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>Přidání třídy knihovny MFC z knihovny typů

Tohoto průvodce použijte k vytvoření třídy knihovny MFC z rozhraní dostupné knihovny typů. Můžete přidat do třídy knihovny MFC [aplikace knihovny MFC](../../mfc/reference/creating-an-mfc-application.md), [knihovny MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md), nebo [ovládací prvek ActiveX knihovny MFC](../../mfc/reference/creating-an-mfc-activex-control.md).

> [!NOTE]
>  Není nutné k vytvoření projektu knihovny MFC s podporou pro přidání třídy z knihovny typů automatizace.

Knihovna typů obsahuje binární popis rozhraní vystavené komponentou, definování metody společně s jejich parametry a návratové typy. Knihovna typů musí být zaregistrovaný, aby se zobrazí v **dostupné knihovny typů** seznamu v přidání třídy z Průvodce knihovnou typů. Viz "uvnitř Distributed COM: Knihovny typů a jazyk integrace "v knihovně MSDN pro další informace.

### <a name="to-add-an-mfc-class-from-a-type-library"></a>Přidání třídy knihovny MFC z knihovny typů

1. V jednom **Průzkumníka řešení** nebo [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na název projektu, ke kterému chcete přidat třídu.

1. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat třídu**.

1. V [přidat třídu](../../ide/add-class-dialog-box.md) dialogové okno, v podokně šablon, klikněte na tlačítko **třída knihovny MFC z Typelib**a potom klikněte na tlačítko **otevřít** zobrazíte [přidat třídu z Průvodce knihovnou typů ](../../mfc/reference/add-class-from-typelib-wizard.md).

V průvodci můžete přidat více než jedna třída v knihovně typů. Podobně přidáním tříd z více než jeden typ knihovny v rámci jedné relace průvodce.

Průvodce vytvoří třídy knihovny MFC, odvozený z [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), pro každé rozhraní, kterou přidáte z vybrané knihovny typů. `COleDispatchDriver` implementuje na straně klienta automatizaci OLE.

## <a name="see-also"></a>Viz také:

[Klienti automatizace](../../mfc/automation-clients.md)<br/>
[Klienti automatizace: Použití knihoven typů](../../mfc/automation-clients-using-type-libraries.md)
