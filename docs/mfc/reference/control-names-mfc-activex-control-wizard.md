---
title: Názvy ovládacích prvků, Průvodce ovládacím prvkem ActiveX v prostředí MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.names
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
ms.openlocfilehash: e7eb1686f191e3bfc60632447978e16ff48b2ab8
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448587"
---
# <a name="control-names-mfc-activex-control-wizard"></a>Názvy ovládacích prvků, Průvodce ovládacím prvkem ActiveX v prostředí MFC

Zadejte názvy pro ovládací prvek třídy a třídy stránky vlastností, názvy typů a zadejte identifikátory pro ovládací prvek. S výjimkou produktů **krátký název**, všechna ostatní pole lze nezávisle upravovat. Pokud se změní text pro **krátký název**, změny se projeví v názvech všechna ostatní pole na této stránce. Toto chování je navržené tak, aby všechny názvy jednoduše rozpoznatelným názvem za vás při vývoji ovládacího prvku.

- **Krátký název**

   Zadejte zkrácený název ovládacího prvku. Ve výchozím nastavení, tento název je založen na názvu projektu, který jste zadali v **nový projekt** dialogové okno. Název, který poskytnete určuje názvy tříd, názvy typů a identifikátory typu, pokud nezměníte těchto polí samostatně.

- **Název třídy ovládacího prvku**

   Ve výchozím nastavení, název třídy ovládacího prvku je založen na krátký název s `C` jako předponu a `Ctrl` jako příponu. Například pokud krátký název je `Price`, je název třídy ovládacího prvku `CPriceCtrl`.

- **Soubor .h ovládacího prvku**

   Ve výchozím nastavení, název souboru hlaviček je založen na krátký název s `Ctrl` jako příponu a `.h` jako příponu souboru. Například pokud krátký název je `Price`, název souboru hlaviček je `PriceCtrl.h`. Název v tomto poli by měl odpovídat názvu třídy ovládacího prvku.

- **Soubor .cpp ovládacího prvku**

   Ve výchozím nastavení, název souboru hlaviček je založen na krátký název s `Ctrl` jako příponu a `.cpp` jako příponu souboru. Například pokud krátký název je `Price`, název souboru hlaviček je `PriceCtrl.cpp`. Název v tomto poli by měl odpovídat názvu záhlaví.

- **Název typu ovládacího prvku**

   Ve výchozím nastavení, název typu ovládacího prvku založené na krátký název, za nímž následuje `Control`. Například pokud krátký název je `Price`, je název třídy typu ovládacího prvku `Price Control`. Pokud změníte hodnotu v tomto poli, ujistěte se, že název označuje dědičnosti.

- **ID typu ovládacího prvku**

   Nastaví ID ovládacího prvku typu třídy ovládacího prvku. Ovládací prvek zapíše tento řetězec do registru, když se přidá do projektu. Aplikace typu kontejner použít tento řetězec pro vytvoření instance ovládacího prvku.

   Ve výchozím nastavení, ID typu ovládacího prvku podle názvu projektu, který jste určili v **nový projekt** dialogové okno a krátký název. Tento název by měl odpovídat názvu typu.

   Ve výchozím nastavení zobrazí ID typu ovládacího prvku následujícím způsobem:

   *ProjectName.ShortName*Ctrl.1

   Pokud změníte v tomto dialogovém okně krátký název, ID typu ovládacího prvku se zobrazí takto:

   *ProjectName.NewShortName*Ctrl.1

- **Název třídy stránky vlastností**

   Ve výchozím nastavení, název třídy stránky vlastností je založen na krátký název s `C` jako předponu a `PropPage` jako příponu. Například pokud krátký název je `Price`, je název třídy stránky vlastností `CPricePropPage`. Tento název by měl odpovídat názvu třídy ovládacího prvku s příponou `PropPage`.

- **Soubor .h stránky vlastností**

   Ve výchozím nastavení je název souboru záhlaví stránky vlastností založen na krátký název s `PropPage` jako příponu a `.h` jako příponu souboru. Například pokud krátký název je `Price`, je název souboru záhlaví stránky vlastností `PricePropPage.h`. Tento název by měl odpovídat názvu třídy.

- **Soubor .cpp stránky vlastností**

   Ve výchozím nastavení je název souboru implementace stránky vlastností založen na krátký název s `PropPage` jako příponu a `.cpp` jako příponu souboru. Například pokud krátký název je `Price`, je název souboru záhlaví stránky vlastností `PricePropPage.cpp`. Tento název by měl odpovídat názvu záhlaví souboru.

- **Název typu stránky vlastností**

   Ve výchozím nastavení, název typu stránky vlastností vychází krátký název, za nímž následuje `Property Page`. Například pokud krátký název je `Price`, je název typu stránky vlastností `Price Property Page`. Pokud změníte hodnotu v tomto poli, ujistěte se, že název označuje třídě ovládacího prvku.

- **ID typu stránky vlastností**

   Nastaví ID třídy stránky vlastností. Ovládací prvek zapíše tento řetězec v registru při použití do projektu. Aplikace typu kontejner pro tento řetězec používá k vytvoření instance stránku vlastností ovládacího prvku.

   Ve výchozím nastavení, ID typu stránky vlastností podle názvu projektu, který jste určili v **nový projekt** dialogové okno a krátký název. Tento název by měl odpovídat názvu typu.

   Ve výchozím nastavení zobrazí se následující ID typu stránky vlastností:

   *ProjectName.ShortName*PropPage.1

   Pokud změníte v tomto dialogovém okně krátký název, ID typu stránky vlastností se zobrazí takto:

   *ProjectName.NewShortName*PropPage.1

## <a name="see-also"></a>Viz také:

[Průvodce ovládacím prvkem ActiveX v prostředí MFC](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Nastavení aplikace, Průvodce ovládacím prvkem ActiveX v prostředí MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[Nastavení ovládacího prvku, Průvodce ovládacím prvkem ActiveX v prostředí MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)<br/>
[Soubor typy vytvořené pro vizuál C++ projekty](../../build/reference/file-types-created-for-visual-cpp-projects.md)

