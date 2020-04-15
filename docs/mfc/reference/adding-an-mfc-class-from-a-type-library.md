---
title: Přidání třídy knihovny MFC z knihovny typů
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: bf9c763a215a4880d5b0ad206f6a347341fea9eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371726"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>Přidání třídy knihovny MFC z knihovny typů

Tento průvodce slouží k vytvoření třídy knihovny MFC z rozhraní v dostupné knihovně typů. Třídu knihovny MFC můžete přidat do [aplikace knihovny MFC](../../mfc/reference/creating-an-mfc-application.md), [knihovny MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)nebo [ovládacího prvku ActiveX knihovny MFC](../../mfc/reference/creating-an-mfc-activex-control.md).

> [!NOTE]
> Není nutné vytvářet projekt knihovny MFC s povolenou automatizací pro přidání třídy z knihovny typů.

Knihovna typů obsahuje binární popis rozhraní vystavených komponentou, definující metody spolu s jejich parametry a návratové typy. Aby se knihovna typů zaregistrovala, aby se zobrazila v seznamu **Dostupné knihovny typů** v Průvodci přidáním třídy z typelib. Další informace naleznete v části Vnitřní distribuované com: knihovny typů a jazyková integrace v knihovně MSDN.

### <a name="to-add-an-mfc-class-from-a-type-library"></a>Přidání třídy knihovny MFC z knihovny typů

1. V **Průzkumníku řešení** nebo [zobrazení třídy](/visualstudio/ide/viewing-the-structure-of-code)klikněte pravým tlačítkem myši na název projektu, do kterého chcete přidat třídu.

1. V místní nabídce klikněte na **Přidat**a potom klikněte na **Přidat třídu**.

1. V dialogovém okně [Přidat třídu](../../ide/add-class-dialog-box.md) klikněte v podokně Šablony na **položku Třída knihovny MFC z typeliba**a potom klepnutím na **tlačítko Otevřít** zobrazte [Průvodce přidáním třídy z funkce Typelib](../../mfc/reference/add-class-from-typelib-wizard.md).

V průvodci můžete přidat více než jednu třídu do knihovny typů. Podobně můžete přidat třídy z více než jedné knihovny typů v jedné relaci průvodce.

Průvodce vytvoří třídu knihovny MFC odvozenou z [cOleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)pro každé rozhraní, které přidáte z vybrané knihovny typů. `COleDispatchDriver`implementuje klientskou stranu automatizace OLE.

## <a name="see-also"></a>Viz také

[Klienti automatizace](../../mfc/automation-clients.md)<br/>
[Klienti automatizace: Použití knihoven typů](../../mfc/automation-clients-using-type-libraries.md)
