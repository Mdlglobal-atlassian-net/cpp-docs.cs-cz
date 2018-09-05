---
title: Přidání ovládacího prvku (ATL – tutoriál, část 2) | Dokumentace Microsoftu
ms.custom: get-started-article
ms.date: 06/18/2018
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac4f3e1460dc4601e15065cb7b968153bd928c87
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762857"
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>Přidání ovládacího prvku (ATL – tutoriál, část 2)

V tomto kroku přidat ovládací prvek do projektu, jejich vytváření a testování na webové stránce.

## <a name="procedures"></a>Procedury

#### <a name="to-add-an-object-to-an-atl-project"></a>Přidání objektu do projektu ATL

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt mnohoúhelník.

2. Přejděte na **přidat** na místní nabídku a klikněte na **nová položka** v podnabídce.

     **Přidat novou položku** zobrazí se dialogové okno. Ve stromové struktuře na levé straně jsou uvedeny různé kategorie objektů.

3. Klikněte na tlačítko **ATL** složky.

4. V seznamu šablon na pravé straně vyberte **ovládací prvek ATL**. Klikněte na tlačítko **přidat**. Otevře se Průvodce ovládacím prvkem ATL a nakonfigurujete ovládací prvek.

5. Typ `PolyCtl` jako krátký název a Všimněte si, že ostatní pole jsou automaticky vyplněna. Neklikejte na **Dokončit** ještě, protože je potřeba udělat nějaké změny.

Průvodce ovládacími prvky ATL **názvy** stránka obsahuje následující pole:

|Pole|Obsah|
|-----------|--------------|
|**Krátký název**|Název, který jste zadali pro ovládací prvek.|
|**Třída**|Název třídy C++ vytvořený pro implementaci ovládacího prvku.|
|**soubor .h**|Soubor vytvořen tak, aby obsahovala definice třídy jazyka C++.|
|**soubor .cpp**|Soubor vytvořen tak, aby obsahovala implementaci třídy C++.|
|**CoClass**|Název třídy komponenty pro tento ovládací prvek.|
|**Rozhraní**|Název rozhraní, ve kterém ovládací prvek implementuje své vlastní metody a vlastnosti.|
|**Typ**|Popis pro ovládací prvek.|
|**ProgID**|Čitelný název, který slouží k vyhledání CLSID ovládacího prvku.|

Je nutné provést několik dalších nastavení v průvodci knihovny ATL ovládacího prvku.

#### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>Povolení podpory pro bohaté chybové informace a spojovací body

1. Klikněte na tlačítko **možnosti** otevřít **možnosti** stránky.

2. Vyberte **spojovací body** zaškrtávací políčko. Tím se vytvoří podpora pro odchozí rozhraní v souboru IDL.

Můžete provést také ovládací prvek jako Vložitelný, což znamená, že lze jej vkládat do aplikace, které podporují vložené objekty, jako je Excel nebo Word.

#### <a name="to-make-the-control-insertable"></a>Chcete-li ovládací prvek jako Vložitelný

1. Klikněte na tlačítko **vzhled** otevřít **vzhled** stránky.

2. Vyberte **Vložitelný** zaškrtávací políčko.

Mnohoúhelník zobrazený v objektu bude mít plnou barvu, takže budete muset přidat `Fill Color` vlastnost zásobníku.

#### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>Přidání uložené vlastnosti Barva výplně a vytvoření ovládacího prvku

1. Klikněte na tlačítko **uložené vlastnosti** otevřít **uložené vlastnosti** stránky.

2. V části **nepodporuje**, procházejte seznam možných uložených vlastností. Dvakrát klikněte na panel `Fill Color` ji chcete přesunout **podporované** seznamu.

3. Tímto dokončíte možnosti ovládacího prvku. Klikněte na tlačítko **Dokončit**.

Při tvorbě ovládacího prvku, došlo k několika změnám kódu a přidání souboru. Následující soubory byly vytvořeny:

|Soubor|Popis|
|----------|-----------------|
|PolyCtl.h|Obsahuje implementaci třídy C++ `CPolyCtl`.|
|PolyCtl.cpp|Obsahuje zbývající části `CPolyCtl`.|
|PolyCtl.rgs|Textový soubor, který obsahuje skript registru používaný k registraci ovládacího prvku.|
|PolyCtl.htm|Webová stránka obsahující odkaz na nově vytvořený ovládací prvek.|

Průvodce také provedl následující změny kódu:

- Přidá `#include` příkazu do souborů stdafx.h a stdafx.cpp zahrnout knihovny ATL soubory potřebné pro podpůrné ovládací prvky.

- Změněný Polygon.idl zahrnuje podrobnosti nového ovládacího prvku.

- Přidat nový ovládací prvek do mapy objektu v Polygon.cpp.

Nyní můžete vytvořit ovládací prvek a vidět ji v akci.

## <a name="building-and-testing-the-control"></a>Vytváření a testování ovládacího prvku

#### <a name="to-build-and-test-the-control"></a>Pro vytváření a testování ovládacího prvku

1. Na **sestavení** nabídky, klikněte na tlačítko **sestavit mnohoúhelník**.

     Po dokončení sestavení ovládacího prvku klikněte pravým tlačítkem na soubor PolyCtl.htm v **Průzkumníka řešení** a vyberte **zobrazit v prohlížeči**. Zobrazí se webová stránka HTML obsahující ovládací prvek. Zobrazí se stránka s názvem "Testovací stránka ATL 8.0 pro objekt PolyCtl" a text **PolyCtl**. Toto je váš ovládací prvek.

> [!NOTE]
>  Po dokončení tohoto kurzu, pokud se zobrazí chybové hlášení, pokud nelze vytvořit soubor knihovny DLL, zavřete soubor PolyCtl.htm a kontejner testu ovládacího prvku ActiveX a znovu sestavte řešení. Pokud stále nelze vytvořit knihovnu DLL, restartujte počítač nebo se odhlaste (Pokud používáte Terminálové služby).

V dalším kroku přidáte vlastní vlastnost do ovládacího prvku.

[Zpátky ke kroku 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [ke kroku 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)

## <a name="see-also"></a>Viz také

[Kurz](../atl/active-template-library-atl-tutorial.md)

