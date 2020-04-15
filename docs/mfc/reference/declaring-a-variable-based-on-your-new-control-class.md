---
title: Deklarace proměnné založené na nové třídě ovládacího prvku
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.control.variable
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
ms.openlocfilehash: 994f81524001a80d1cf0dd3783b9de742d61e84d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365849"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>Deklarace proměnné založené na nové třídě ovládacího prvku

Po vytvoření třídy řízení knihovny MFC můžete deklarovat proměnnou na základě ní. Chcete-li poskytnout kontext pro novou proměnnou, musíte otevřít editor dialogů a upravit dialogové okno, ve kterém chcete použít opakovaně použitelný ovládací prvek. Dialogové okno také musí mít již třídu přidruženou. Informace o používání editoru dialogů naleznete v [tématu Dialog Editor](../../windows/dialog-editor.md).

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>Deklarování proměnné na základě vaší opakovaně použitelné třídy

1. Při úpravách dialogového okna přetáhněte ovládací prvek stejného typu jako základní třída nového ovládacího prvku z panelu nástrojů Ovládací prvky do dialogového okna.

1. Umístěte ukazatel myši nad zrušený ovládací prvek.

1. Při stisknutí klávesy CTRL poklepejte na ovládací prvek.

   Zobrazí se dialogové okno [Přidat proměnnou člena.](../../ide/add-member-variable-wizard.md)

1. V poli **Access** vyberte správný přístup ovládacího prvku.

1. Klepněte na zaškrtávací políčko **Ovládací prvek.**

1. Do pole **Název proměnné** zadejte název.

1. V **části Kategorie**klepněte na **položku Control**.

1. V seznamu **ID ovládacího prvku** vyberte ovládací prvek, který jste přidali. V seznamu **Typ proměnné** by měl být zobrazen správný typ proměnné a pole **Typ ovládacího prvku** by mělo být zobrazeno správný typ ovládacího prvku.

1. Do pole **Komentář** přidejte všechny komentáře, které se chcete zobrazit v kódu.

1. Klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také

[Mapování zpráv na funkce](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Přepsání virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Obslužná rutina zprávy knihovny MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigace ve struktuře třídy](../../ide/navigate-code-cpp.md)
