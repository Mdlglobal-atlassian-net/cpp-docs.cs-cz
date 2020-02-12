---
title: Přidání vlastnosti do ovládacího prvku (ATL – tutoriál, část 3)
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
ms.openlocfilehash: 288dc9f5af57c02639d15a9a971419a633cfc08d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127584"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>Přidání vlastnosti do ovládacího prvku (ATL – tutoriál, část 3)

`IPolyCtl` je rozhraní, které obsahuje vlastní metody a vlastnosti ovládacího prvku a přidáte do něj vlastnost.

### <a name="to-add-the-property-definitions-to-your-project"></a>Přidání definice vlastností do projektu

1. V **zobrazení tříd**rozbalte větev `Polygon`.

1. Pravým tlačítkem myši klikněte na `IPolyCtl`.

1. V místní nabídce klikněte na **Přidat**a potom klikněte na **Přidat vlastnost**. Zobrazí se průvodce **přidáním vlastnosti** .

1. Jako **název vlastnosti**zadejte `Sides`.

1. V rozevíracím seznamu **typ vlastnosti**vyberte možnost `short`.

1. Kliknutím na tlačítko **OK** dokončete přidávání vlastnosti.

1. Z **Průzkumník řešení**otevřete mnohoúhelník. idl a na konci `IPolyCtl : IDispatch` rozhraní nahraďte následující řádky:

    ```cpp
    short get_Sides();
    void set_Sides(short value);
    ```

    následující adresou:

    ```cpp
    [propget, id(1), helpstring("property Sides")] HRESULT Sides([out, retval] short *pVal);
    [propput, id(1), helpstring("property Sides")] HRESULT Sides([in] short newVal);
    ```

1. Z **Průzkumník řešení**otevřete PolyCtl. h a přidejte následující řádky za definici `m_clrFillColor`:

    [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

I když máte nyní k dispozici kostru funkcí pro nastavení a načtení vlastnosti a proměnné pro uložení vlastnosti, musíte implementovat funkce odpovídajícím způsobem.

### <a name="to-update-the-get-and-put-methods"></a>Aktualizace metod get a Put

1. Nastavte výchozí hodnotu `m_nSides`. Nastaví výchozí tvar trojúhelníku přidáním čáry do konstruktoru v PolyCtl. h:

    [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

1. Implementujte metody `Get` a `Put`. Deklarace funkce `get_Sides` a `put_Sides` byly přidány do PolyCtl. h. Nyní přidejte kód pro `get_Sides` a `put_Sides` do PolyCtl. cpp následujícím způsobem:

    [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

Metoda `get_Sides` vrátí aktuální hodnotu vlastnosti `Sides` prostřednictvím ukazatele `pVal`. V metodě `put_Sides` kód zajišťuje, že uživatel nastaví vlastnost `Sides` na přijatelnou hodnotu. Minimální hodnota musí být 3 a vzhledem k tomu, že pole bodů bude použito pro každou stranu, 100 je přiměřeným omezením pro maximální hodnotu.

Nyní máte vlastnost s názvem `Sides`. V dalším kroku změníte kód pro kreslení, abyste ho mohli používat.

[Zpátky ke kroku 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [na krok 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)

## <a name="see-also"></a>Viz také

[Kurz](../atl/active-template-library-atl-tutorial.md)
