---
title: Názvy ovládacích prvků, Průvodce ovládacím prvkem ActiveX v prostředí MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.names
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
ms.openlocfilehash: eff7b537e7fe5c19d10cce8766557a3d1ff49342
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077508"
---
# <a name="control-names-mfc-activex-control-wizard"></a>Názvy ovládacích prvků, Průvodce ovládacím prvkem ActiveX v prostředí MFC

Zadejte názvy pro třídu ovládacího prvku a třídu stránky vlastností, názvy typů a identifikátory typů pro váš ovládací prvek. S výjimkou **krátkého názvu**lze všechna ostatní pole upravovat nezávisle. Pokud změníte text pro **krátký název**, změna se projeví v názvech všech ostatních polí na této stránce. Toto chování při pojmenovávání je navržené tak, aby byly všechny názvy snadno identifikovatelné při vývoji ovládacího prvku.

- **Krátký název**

   Zadejte zkrácený název ovládacího prvku. Ve výchozím nastavení je tento název založen na názvu projektu, který jste zadali v dialogovém okně **Nový projekt** . Název, který zadáte, určuje názvy tříd, názvy typů a identifikátory typů, pokud tato pole nezměníte jednotlivě.

- **Název třídy ovládacího prvku**

   Ve výchozím nastavení je název třídy ovládacího prvku založený na krátkém názvu, s `C` jako předponou a `Ctrl` jako příponou. Například pokud je krátký název vašeho ovládacího prvku `Price`, název třídy ovládacího prvku je `CPriceCtrl`.

- **Soubor. h ovládacího prvku**

   Ve výchozím nastavení je název hlavičkového souboru založen na krátkém názvu s `Ctrl` jako příponou a `.h` jako příponou souboru. Například pokud je krátký název vašeho ovládacího prvku `Price`, název hlavičkového souboru je `PriceCtrl.h`. Název v tomto poli by měl odpovídat názvu třídy ovládacího prvku.

- **Soubor. cpp ovládacího prvku**

   Ve výchozím nastavení je název hlavičkového souboru založen na krátkém názvu s `Ctrl` jako příponou a `.cpp` jako příponou souboru. Například pokud je krátký název vašeho ovládacího prvku `Price`, název hlavičkového souboru je `PriceCtrl.cpp`. Název v tomto poli by měl odpovídat názvu záhlaví.

- **Název typu ovládacího prvku**

   Ve výchozím nastavení je název typu ovládacího prvku založený na krátkém názvu, následovaným `Control`. Například pokud je krátký název vašeho ovládacího prvku `Price`, název typu třídy ovládacího prvku je `Price Control`. Pokud změníte hodnotu v tomto poli, ujistěte se, že název označuje dědičnost.

- **ID typu ovládacího prvku**

   Nastaví ID typu ovládacího prvku třídy ovládacího prvku. Ovládací prvek zapíše tento řetězec do registru při jeho přidání do projektu. Aplikace typu kontejner používají tento řetězec k vytvoření instance ovládacího prvku.

   Ve výchozím nastavení je identifikátor typu ovládacího prvku založen na názvu projektu, který jste uvedli v dialogovém okně **Nový projekt** , a v krátkém názvu. Tento název by měl odpovídat názvu typu.

   Ve výchozím nastavení se ID typu ovládacího prvku zobrazí takto:

   *ProjectName. krátký* název CTRL. 1

   Pokud v tomto dialogovém okně změníte krátký název, ID typu ovládacího prvku se zobrazí takto:

   *ProjectName. NewShortName* CTRL. 1

- **Název třídy stránky vlastností**

   Ve výchozím nastavení je název třídy stránky vlastností založen na krátkém názvu, s `C` jako předponou a `PropPage` jako příponou. Například pokud je krátký název vašeho ovládacího prvku `Price`, název třídy stránky vlastností je `CPricePropPage`. Tento název by měl odpovídat názvu třídy ovládacího prvku, který je připojený pomocí `PropPage`.

- **Stránky vlastností. h – soubor**

   Ve výchozím nastavení je název souboru hlaviček stránky vlastností založený na krátkém názvu, s jako `PropPage` jako příponou a `.h` jako příponou souboru. Například pokud je krátký název vašeho ovládacího prvku `Price`, název souboru hlaviček stránky vlastností je `PricePropPage.h`. Tento název by měl odpovídat názvu třídy.

- **Stránky vlastností. cpp – soubor**

   Ve výchozím nastavení je název implementačního souboru stránky vlastností založený na krátkém názvu, s `PropPage` jako příponou a `.cpp` jako příponou souboru. Například pokud je krátký název vašeho ovládacího prvku `Price`, název souboru hlaviček stránky vlastností je `PricePropPage.cpp`. Tento název by měl odpovídat názvu hlavičkového souboru.

- **Název typu stránky vlastností**

   Ve výchozím nastavení je název typu stránky vlastností založený na krátkém názvu následovaný `Property Page`. Například pokud je krátký název vašeho ovládacího prvku `Price`, název typu stránky vlastností je `Price Property Page`. Pokud změníte hodnotu v tomto poli, ujistěte se, že název označuje třídu ovládacího prvku.

- **ID typu stránky vlastností**

   Nastaví ID třídy stránky vlastností. Ovládací prvek zapíše tento řetězec v registru, když je použit pro projekt. Aplikace typu kontejner používá tento řetězec k vytvoření instance stránky vlastností ovládacího prvku.

   Ve výchozím nastavení je ID typu stránky vlastností založeno na názvu projektu, který jste uvedli v dialogovém okně **Nový projekt** , a v krátkém názvu. Tento název by měl odpovídat názvu typu.

   Ve výchozím nastavení se ID typu stránky Vlastnosti zobrazí takto:

   *ProjectName. krátký* název Stránky vlastností. 1

   Pokud v tomto dialogovém okně změníte krátký název, zobrazí se ID typu stránky vlastnosti takto:

   *ProjectName. NewShortName* Stránky vlastností. 1

## <a name="see-also"></a>Viz také

[Průvodce ovládacím prvkem ActiveX v prostředí MFC](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Nastavení aplikace, Průvodce ovládacím prvkem ActiveX v prostředí MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[Nastavení ovládacího prvku, Průvodce ovládacím prvkem ActiveX v prostředí MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)<br/>
[Typy souborů vytvořených pro projekty sady C++ Visual Studio](../../build/reference/file-types-created-for-visual-cpp-projects.md)
