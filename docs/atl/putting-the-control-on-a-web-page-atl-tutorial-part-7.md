---
title: Vložení ovládacího prvku na webovou stránku (ATL – tutoriál, část 7)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
ms.openlocfilehash: baf0ca56ae7512ac76f64b29e3060e0749c083c1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297447"
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>Vložení ovládacího prvku na webovou stránku (ATL – tutoriál, část 7)

Ovládací prvek je nyní dokončena. Chcete-li zobrazit práci v reálné situaci ovládacího prvku, umístěte ho na webové stránce. Soubor HTML, který obsahuje ovládací prvek byl vytvořen při definování vašeho ovládacího prvku. Otevřete soubor PolyCtl.htm z **Průzkumníka řešení**, a vy vidíte ovládacího prvku na webové stránce.

V tomto kroku přidáte funkci do ovládacího prvku a skriptovat webovou stránku pro reakci na události. Upravíte také ovládací prvek umožňuje aplikaci Internet Explorer vědět, že ovládací prvek je bezpečný pro skriptování.

## <a name="adding-new-functionality"></a>Přidání nové funkce

### <a name="to-add-control-features"></a>Chcete-li přidat ovládací prvek funkce

1. Otevřete PolyCtl.cpp a nahraďte následujícím kódem:

    ```cpp
    if (PtInRegion(hRgn, xPos, yPos))
        Fire_ClickIn(xPos, yPos);
    else
        Fire_ClickOut(xPos, yPos);
    ```

    with

    ```cpp
    short temp = m_nSides;
    if (PtInRegion(hRgn, xPos, yPos))
    {
        Fire_ClickIn(xPos, yPos);
        put_Sides(++temp);
    }
    else
    {
        Fire_ClickOut(xPos, yPos);
        put_Sides(--temp);
    }
    ```

Tvar se nyní přidat nebo odebrat strany v závislosti na tom, kde klikněte na.

## <a name="scripting-the-web-page"></a>Skriptování webové stránky

Ovládací prvek zatím nic nedělá, takže upravte webovou stránku v reakci na odeslané události.

### <a name="to-script-the-web-page"></a>Chcete-li skriptovat webovou stránku

1. Otevřete PolyCtl.htm a vyberte zobrazení HTML. Přidejte následující řádky do kódu HTML. Měly by být přidány po `</OBJECT>` ale předtím, než `</BODY>`.

    ```html
    <SCRIPT LANGUAGE="VBScript">
    <!--
        Sub PolyCtl_ClickIn(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - adding side")
        End Sub
        Sub PolyCtl_ClickOut(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - removing side")
        End Sub
    -->
    </SCRIPT>
    ```

1. Uložte soubor HTM.

Přidali jste některý kód jazyka VBScript, který získá vlastnost Sides z ovládacího prvku a zvýší počet stran o 1, pokud kliknete dovnitř ovládacího prvku. Pokud klepnete na tlačítko mimo ovládací prvek, snížíte počet stran o jednu.

## <a name="indicating-that-the-control-is-safe-for-scripting"></a>Indikuje, že ovládací prvek je bezpečný pro skriptování

Můžete zobrazit webovou stránku pomocí ovládacího prvku v aplikaci Internet Explorer nebo ještě pohodlněji pomocí zobrazení webového prohlížeče, které jsou součástí Visual C++. Chcete-li zobrazit ovládací prvek ve webovém prohlížeči, pravým tlačítkem myši na PolyCtl.htm a klikněte na tlačítko **zobrazit v prohlížeči**.

> [!NOTE]
> Pokud ovládací prvek není viditelný, vědět, že některé prohlížeče vyžadovat úpravy nastavení spuštění ovládacích prvků ActiveX. Najdete v prohlížeči na dokumentaci o tom, jak povolit ovládací prvky ActiveX.

Podle aktuálního nastavení zabezpečení aplikace Internet Explorer, může se zobrazit dialogové okno oznamující, že ovládací prvek nemusí být skript bezpečný a může potenciálně způsobit poškození výstrahy zabezpečení. Například, pokud jste měli ovládací prvek, který zobrazil soubor, ale měl rovněž `Delete` metodě, která se odstranil se soubor, mělo by být bezpečné Pokud jste ho pouze zobrazili na stránce. Mělo by není bezpečné použít skript, protože někdo může volat `Delete` metody.

> [!IMPORTANT]
> Pro účely tohoto kurzu můžete změnit nastavení zabezpečení v aplikaci Internet Explorer ke spuštění ovládacích prvků ActiveX, které nejsou označeny jako bezpečné. V Ovládacích panelech klikněte na tlačítko **vlastnosti Internetu** a klikněte na tlačítko **zabezpečení** pro změnu příslušných nastavení. Po dokončení kurzu změňte nastavení zabezpečení zpět do původního stavu.

Můžete programově upozornit aplikaci Internet Explorer, že nemusí zobrazit dialogové okno upozornění zabezpečení pro tento konkrétní ovládací prvek. Můžete to provedete `IObjectSafety` rozhraní a ATL dodá implementaci tohoto rozhraní ve třídě [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md). Chcete-li přidat rozhraní do ovládacího prvku, přidejte `IObjectSafetyImpl` do seznamu zděděných tříd a přidejte položku do mapy modelu COM. pro něj.

### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>Přidat IObjectSafetyImpl do ovládacího prvku

1. Přidejte následující řádek na konec seznamu zděděné třídy v souboru PolyCtl.h a přidejte čárku na předchozí řádek:

    [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]

1. Do mapy modelu COM v souboru PolyCtl.h přidejte následující řádek:

    [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]

## <a name="building-and-testing-the-control"></a>Vytváření a testování ovládacího prvku

Vytvoření ovládacího prvku. Po dokončení sestavení, otevřete PolyCtl.htm znovu v prohlížeči. Tentokrát by měl webovou stránku přímo bez zobrazí **výstraha zabezpečení** dialogové okno. Klikněte dovnitř mnohoúhelníku; počet stran se zvýší o jedna. Klikněte mimo mnohoúhelník pro snížení počtu stran.

[Zpět na krok 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="next-steps"></a>Další kroky

Tímto dokončíte kurz ATL. Odkazy na další informace o poskytovateli ATL naleznete v části [úvodní stránka ATL](../atl/active-template-library-atl-concepts.md).

## <a name="see-also"></a>Viz také:

[Kurz](../atl/active-template-library-atl-tutorial.md)
