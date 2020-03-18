---
title: Přidání obslužné rutiny události
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
- event handler wizard [C++]
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
ms.openlocfilehash: 0d852991c29281a7ecf912bd3d764d9916ef10f7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447504"
---
# <a name="add-an-event-handler"></a>Přidání obslužné rutiny události

V editoru prostředků můžete přidat novou obslužnou rutinu události nebo upravit existující obslužnou rutinu události pro ovládací prvek dialogové okno pomocí [Průvodce obslužnou rutinou události](#event-handler-wizard).

Do třídy, která implementuje dialogové okno, můžete přidat událost pomocí [okno Vlastnosti](/visualstudio/ide/reference/properties-window). Chcete-li přidat událost do jiné třídy než do třídy dialogového okna, použijte Průvodce obslužnou rutinou události.

**Přidání obslužné rutiny události do ovládacího prvku dialogové okno:**

1. Dvojím kliknutím na prostředek dialogového okna v [prostředky](../windows/how-to-create-a-resource-script-file.md#create-resources) otevřete dialogové okno prostředek, který obsahuje ovládací prvek v [editoru dialogových oken](../windows/dialog-editor.md).

1. Klikněte pravým tlačítkem myši na ovládací prvek, pro který chcete zpracovat událost oznámení.

1. V místní nabídce vyberte možnost **Přidat obslužnou rutinu události** k zobrazení Průvodce obslužnou rutinou události.

1. Vyberte událost v poli **typ zprávy** , která se přidá do třídy vybrané v **seznamu třída** .

1. Přijměte výchozí název v poli **název obslužné rutiny funkce** nebo zadejte název podle svého výběru.

1. Vyberte **Přidat a upravit** pro přidání obslužné rutiny události do projektu a otevřete textový editor na nové funkci a přidejte odpovídající kód obslužné rutiny události.

   Pokud vybraný typ zprávy již obsahuje obslužnou rutinu události pro vybranou třídu, není možnost **Přidat a upravit** k dispozici a **kód pro úpravy** je k dispozici. Výběrem **Upravit kód** otevřete textový editor v existující funkci.

Alternativně můžete přidat obslužné rutiny událostí z [okno Vlastnosti](/visualstudio/ide/reference/properties-window). Další informace naleznete v tématu [Přidání obslužných rutin událostí pro ovládací prvky dialogového okna](../windows/adding-event-handlers-for-dialog-box-controls.md).

## <a name="in-this-section"></a>V tomto oddílu

- [Průvodce obslužnou rutinou události](#event-handler-wizard)

## <a name="event-handler-wizard"></a>Průvodce obslužnou rutinou události

Tento průvodce přidá do vámi vybrané třídy obslužnou rutinu události pro ovládací prvek dialogového okna. Pokud přidáte obslužnou rutinu události z [okno Vlastnosti](/visualstudio/ide/reference/properties-window), můžete ji přidat pouze do třídy, která implementuje dialogové okno. Další informace naleznete v tématu [Přidání obslužných rutin událostí pro ovládací prvky dialogového okna](../windows/adding-event-handlers-for-dialog-box-controls.md).

- **Název příkazu**

  Identifikuje vybraný ovládací prvek, pro který se přidá obslužná rutina události. Toto políčko je nedostupné.

- **Typ zprávy**

  Zobrazí seznam aktuálních možných obslužných rutin zpráv pro vybraný ovládací prvek.

- **Název obslužné rutiny funkce**

  Zobrazuje název funkce, která je přidána pro zpracování události. Ve výchozím nastavení je název založen na typu zprávy a příkazu, který předchází `On`. Například pro tlačítko s názvem `IDC_BUTTON1`typ zprávy `BN_CLICKED` zobrazí název obslužné rutiny funkce `OnBnClickedButton1`.

- **Seznam tříd**

  Zobrazí dostupné třídy, do kterých můžete přidat obslužnou rutinu události. Třída pro vybrané dialogové okno je zobrazena červeně.

- **Popis obslužné rutiny**

  Poskytuje popis položky vybrané v poli **typ zprávy** . Toto políčko je nedostupné.

- **Přidat a upravit**

  Přidá popisovač zprávy do vybrané třídy nebo objektu. Otevře také textový editor pro novou funkci, takže můžete přidat kód obslužné rutiny pro oznámení ovládacího prvku.

- **Upravit kód**

  Otevře textový editor pro vybranou existující funkci, takže můžete přidat nebo upravit kód obslužné rutiny oznámení ovládacího prvku.
