---
title: Přidání obslužné rutiny událostí
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.eventhandler.overview
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
- event handler wizard [C++]
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
ms.openlocfilehash: 96e5b8777bb8b0c976277a06e8ad49b3334921fb
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328568"
---
# <a name="add-an-event-handler"></a>Přidání obslužné rutiny událostí

Z editoru prostředků, můžete přidat novou obslužnou rutinu události nebo upravit existující obslužné rutiny události pomocí ovládacího prvku pole dialogového okna [Průvodce obslužnou rutinou události](#event-handler-wizard).

Událost můžete přidat do třídy implementující pomocí dialogového okna pole [okno vlastností](/visualstudio/ide/reference/properties-window). K přidání události do třídy než třídy dialogového okna, použijte Průvodce obslužnou rutinou události.

**Chcete-li přidat obslužnou rutinu události pro ovládací prvek dialogového okna:**

1. Dvakrát klikněte na pole prostředku dialogového okna v [zobrazení prostředků](../windows/how-to-create-a-resource-script-file.md#create-resources) otevřete dialogové okno prostředků pole, která obsahuje ovládací prvek v [editoru dialogového okna](../windows/dialog-editor.md).

1. Klikněte pravým tlačítkem na ovládací prvek, pro kterou chcete zpracovat událost oznámení.

1. V místní nabídce zvolte **přidat obslužnou rutinu události** zobrazíte Průvodce obslužnou rutinou události.

1. Vybrat událost v **typ zprávy** pole můžete přidat do třídy vybraný v **seznamu tříd** pole.

1. Přijměte výchozí název v **název obslužné funkce** pole, nebo zadejte název podle vašeho výběru.

1. Vyberte **přidat a upravit** přidat obslužnou rutinu události do projektu a otevřete textový editor v nové funkci přidat kód pro obslužnou rutinu události.

   Pokud je zvolený typ zpráv, už obslužnou rutinu události pro vybranou třídu **přidat a upravit** není k dispozici, a **upravit kód** je k dispozici. Vyberte **upravit kód** otevřete textový editor v existující funkce.

Alternativně můžete přidat obslužné rutiny událostí z [okno vlastností](/visualstudio/ide/reference/properties-window). Další informace najdete v tématu [přidání obslužné rutiny událostí pro ovládací prvky dialogového okna](../windows/adding-event-handlers-for-dialog-box-controls.md).

## <a name="in-this-section"></a>V tomto oddílu

- [Průvodce obslužnou rutinou události](#event-handler-wizard)

## <a name="event-handler-wizard"></a>Průvodce obslužnou rutinou události

Tento průvodce přidá do vámi vybrané třídy obslužnou rutinu události pro ovládací prvek dialogového okna. Pokud chcete přidat obslužnou rutinu události z [okno vlastností](/visualstudio/ide/reference/properties-window), ho můžete přidat pouze do třídy, která implementuje dialogových oken. Další informace najdete v tématu [přidání obslužné rutiny událostí pro ovládací prvky dialogového okna](../windows/adding-event-handlers-for-dialog-box-controls.md).

- **Název příkazu**

  Určuje vybraný ovládací prvek, pro který se přidá obslužnou rutinu události. Toto pole je k dispozici.

- **Typ zprávy**

  Zobrazí seznam aktuální obslužné rutiny zpráv možné pro vybraný ovládací prvek.

- **Název obslužné rutiny – funkce**

  Zobrazuje název funkce, která se přidá ke zpracování události. Název ve výchozím nastavení je založen na typ zprávy a příkaz předcházený `On`. Například pro tlačítko názvem `IDC_BUTTON1`, typ zprávy `BN_CLICKED` zobrazí název obslužné rutiny funkce `OnBnClickedButton1`.

- **Seznam tříd**

  Zobrazí dostupné třídy, na které můžete přidat obslužnou rutinu události. Třída pro vybrané dialogové okno se zobrazí červeně.

- **Popis obslužné rutiny**

  Poskytuje popis položky vybrané v **typ zprávy** pole. Toto pole je k dispozici.

- **Přidávání a úprava**

  Přidá popisovač zprávy pro vybranou třídu nebo objektu. Proto můžete přidat kód pro obslužnou rutinu pro oznámení ovládacího prvku textového editoru na tuto novou funkci, otevře se také.

- **Úpravy kódu**

  Proto můžete přidat nebo upravit kód pro obslužnou rutinu oznámení ovládací prvek, otevře se textovém editoru na vybrané existující funkce.
