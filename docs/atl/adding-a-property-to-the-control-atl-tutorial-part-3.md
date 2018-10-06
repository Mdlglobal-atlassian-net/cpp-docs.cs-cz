---
title: Přidání vlastnosti do ovládacího prvku (ATL – tutoriál, část 3) | Dokumentace Microsoftu
ms.custom: get-started-article
ms.date: 09/26/2018
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2373d2d703f18824274df158b31023669d8df945
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820463"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>Přidání vlastnosti do ovládacího prvku (ATL – tutoriál, část 3)

`IPolyCtl` je rozhraní, které obsahuje ovládacího prvku vlastní metody a vlastnosti a přidáte do jeho vlastnosti.

### <a name="to-add-the-property-definitions-to-your-project"></a>Chcete-li přidat definice vlastností do projektu

1. V **zobrazení tříd**, rozbalte `Polygon` větve.

1. Klikněte pravým tlačítkem na `IPolyCtl`.

1. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat vlastnost**. **Přidat vlastnost** průvodce se zobrazí.

1. Typ `Sides` jako **název vlastnosti**.

1. V rozevíracím seznamu **typ vlastnosti**vyberte `short`.

1. Klikněte na tlačítko **OK** mohli dokončit přidávání vlastnost.

1. Z **Průzkumníka řešení**Polygon.idl otevřete a nahraďte následující řádky na konci `IPolyCtl : IDispatch` rozhraní:

    ```cpp
    short get_Sides();
    void set_Sides(short value);
    ```

    with

    ```cpp
    [propget, id(1), helpstring("property Sides")] HRESULT Sides([out, retval] short *pVal);
    [propput, id(1), helpstring("property Sides")] HRESULT Sides([in] short newVal);
    ```

1. Z **Průzkumníka řešení**otevřete souboru PolyCtl.h a přidejte následující řádky po definování `m_clrFillColor`:

    [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

I když Teď máte kostru funkce pro nastavení a načtení vlastnost a proměnnou pro uložení vlastnost, je nutné implementovat funkce odpovídajícím způsobem.

### <a name="to-update-the-get-and-put-methods"></a>Aktualizace get a put metody

1. Nastavit výchozí hodnotu `m_nSides`. Nastavit jako výchozí obrazce Trojúhelník konstruktoru v souboru PolyCtl.h přidejte řádek:

    [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

1. Implementace `Get` a `Put` metody. `get_Sides` a `put_Sides` deklarace funkce byly přidány do souboru PolyCtl.h. Teď přidejte kód pro `get_Sides` a `put_Sides` k PolyCtl.cpp následujícím kódem:

    [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

`get_Sides` Metoda vrátí aktuální hodnotu `Sides` vlastnosti prostřednictvím `pVal` ukazatele. V `put_Sides` zajišťuje kód metodu, nastavení uživatele `Sides` vlastnost přijatelné hodnoty. Minimální hodnota musí být 3 a vzhledem k tomu, že pole body se použije pro každé straně, 100, je rozumné limit pro maximální hodnotu.

Teď mají vlastnost zvanou `Sides`. V dalším kroku změníte výkresu kód pro jeho použití.

[Zpátky ke kroku 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [ke kroku 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)

## <a name="see-also"></a>Viz také

[Kurz](../atl/active-template-library-atl-tutorial.md)
