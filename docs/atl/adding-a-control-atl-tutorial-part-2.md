---
title: Přidání ovládacího prvku (ATL – tutoriál, část 2)
ms.custom: get-started-article
ms.date: 08/19/2019
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
ms.openlocfilehash: b7952f42b24c4211a2c44ea71fd17e4f65c3421a
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630700"
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>Přidání ovládacího prvku (ATL – tutoriál, část 2)

V tomto kroku přidáte ovládací prvek do projektu, sestavíte ho a otestujete jej na webové stránce.

## <a name="procedures"></a>Procedury

### <a name="to-add-an-object-to-an-atl-project"></a>Přidání objektu do projektu ATL

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši `Polygon` na projekt.

1. V místní nabídce vyberte možnost **Přidat** a v podnabídce klikněte na položku **Nová položka** .

    Zobrazí se dialogové okno **Přidat novou položku**. Různé kategorie objektů jsou uvedeny ve stromové struktuře vlevo.

1. Klikněte na složku **ATL** .

1. V seznamu šablon na pravé straně vyberte **ovládací prvek ATL**. Klikněte na **Přidat**. Otevře se průvodce **ovládacími prvky ATL** a můžete nakonfigurovat ovládací prvek.

1. Zadejte `PolyCtl` jako krátký název a Všimněte si, že ostatní pole jsou automaticky dokončená. Neklikejte ještě na **Dokončit** , protože musíte udělat nějaké další změny.

Stránka s **názvy** průvodce **ovládacím prvkem ATL** obsahuje následující pole:

|Pole|Obsah|
|-----------|--------------|
|**Krátký název**|Název, který jste zadali pro ovládací prvek.|
|**Třída**|Název C++ třídy vytvořený k implementaci ovládacího prvku.|
|**soubor. h**|Soubor vytvořený tak, aby obsahoval definici C++ třídy.|
|**soubor. cpp**|Soubor vytvořený tak, aby obsahoval implementaci C++ třídy.|
|**CoClass**|Název třídy komponenty pro tento ovládací prvek.|
|**Rozhraní**|Název rozhraní, ve kterém bude ovládací prvek implementovat své vlastní metody a vlastnosti.|
|**Typ**|Popis ovládacího prvku|
|**ProgID**|Čitelný název, který lze použít k vyhledání identifikátoru CLSID ovládacího prvku.|

V průvodci **ovládacími prvky ATL** se musí změnit několik dalších nastavení.

### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>Povolení podpory pro bohatou informaci o chybách a spojovací body

1. Kliknutím na **Možnosti** otevřete stránku **Možnosti** .

1. Zaškrtněte políčko **spojovací body** . Tato možnost vytvoří podporu pro odchozí rozhraní v souboru IDL.

Můžete také přidat rozhraní pro rozšiřování funkcí ovládacího prvku.

### <a name="to-extend-the-controls-functionality"></a>Postup rozšiřování funkcí ovládacího prvku

1. Kliknutím na **rozhraní** otevřete stránku **rozhraní** .

1. Vyberte `IProvideClassInfo2` a kliknutím na šipku **nahoru** ho přesuňte do seznamu **podporovaných** .

1. Vyberte `ISpecifyPropertyPages` a kliknutím na šipku **nahoru** ho přesuňte do seznamu **podporovaných** .

Můžete také nastavit, aby byl ovládací prvek vložený, což znamená, že je možné ho *Vložit*do aplikací podporujících vložené objekty, jako je Excel nebo Word.

### <a name="to-make-the-control-insertable"></a>Chcete-li umožnit vložení ovládacího prvku

1. Kliknutím na tlačítko **vzhled** otevřete stránku **vzhled** .

1. Zaškrtněte políčko **vložitelné** .

Mnohoúhelník zobrazený objektem bude mít plnou barvu výplně, takže je nutné přidat `Fill Color` uloženou vlastnost.

### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>Přidání vlastnosti Barva výplně a vytvoření ovládacího prvku

1. Kliknutím na položku **uložené vlastnosti** otevřete stránku **vlastností** s uloženým stavem.

1. V části **není podporováno**, přejděte dolů na seznam možných stavů uložených vlastností. Vyberte `Fill Color` a kliknutím na šipku **nahoru** ho přesuňte do seznamu **podporovaných** .

1. Zvolte **Dokončit**.

Jak průvodce vytvoří ovládací prvek, dojde k několika změnám kódu a k přidaným souborům. Vytvoří se následující soubory:

|Soubor|Popis|
|----------|-----------------|
|PolyCtl.h|Obsahuje většinu implementace `CPolyCtl` C++ třídy.|
|PolyCtl.cpp|Obsahuje zbývající části `CPolyCtl`.|
|PolyCtl.rgs|Textový soubor, který obsahuje skript registru použitý k registraci ovládacího prvku.|
|PolyCtl.htm|Webová stránka obsahující odkaz na nově vytvořený ovládací prvek.|

Průvodce také provede následující změny kódu:

- `#include` Přidá příkaz do předkompilovaných hlavičkových souborů, aby zahrnovaly soubory ATL nutné pro podpůrné ovládací prvky.

- Změní mnohoúhelník. idl na zahrnutí podrobností nového ovládacího prvku.

- Přidá nový ovládací prvek do mapy objektů v mnohoúhelníku. cpp.

Nyní můžete vytvořit ovládací prvek a zobrazit ho v akci.

## <a name="building-and-testing-the-control"></a>Sestavování a testování ovládacího prvku

### <a name="to-build-and-test-the-control"></a>Sestavení a otestování ovládacího prvku

1. V nabídce **sestavení** klikněte na příkaz **sestavit mnohoúhelník**.

    Jakmile bude ovládací prvek dokončen sestavování, klikněte pravým tlačítkem myši na PolyCtl. htm v **Průzkumník řešení** a vyberte **Zobrazit v prohlížeči**. Zobrazí se webová stránka HTML obsahující ovládací prvek. Měla by se zobrazit Stránka s názvem "testovací stránka ATL 8,0 pro Object PolyCtl" a vaším ovládacím prvkem text PolyCtl.

> [!NOTE]
> Pokud ovládací prvek není viditelný, víte, že některé prohlížeče vyžadují úpravy nastavení pro spouštění ovládacích prvků ActiveX. Informace o tom, jak povolit ovládací prvky ActiveX, najdete v dokumentaci v prohlížeči.

> [!NOTE]
> Pokud při dokončení tohoto kurzu obdržíte chybovou zprávu, že soubor DLL nelze vytvořit, zavřete soubor PolyCtl. htm a kontejner testu ovládacího prvku ActiveX a znovu sestavte řešení. Pokud stále nemůžete vytvořit knihovnu DLL, restartujte počítač nebo se odhlaste, pokud používáte Terminálovou službu.

Dále do ovládacího prvku přidáte vlastní vlastnost.

[Zpět ke kroku 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [Ke kroku 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)

## <a name="see-also"></a>Viz také:

[Kurz](../atl/active-template-library-atl-tutorial.md)
