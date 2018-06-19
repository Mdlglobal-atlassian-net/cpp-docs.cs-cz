---
title: Přidání vlastnosti do ovládacího prvku (ATL – tutoriál, část 3) | Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
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
ms.openlocfilehash: fda9359da6ddc48248874227d58f0c184af45c54
ms.sourcegitcommit: 9b442b44ee912822d06cabec826aac4a8d82ec75
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472083"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>Přidání vlastnosti do ovládacího prvku (ATL – tutoriál, část 3)
`IPolyCtl` je rozhraní, které obsahuje ovládacího prvku vlastní metody a vlastnosti a vlastnosti přidáte k ní.  
  
### <a name="to-add-a-property-using-the-add-property-wizard"></a>Přidání vlastnosti pomocí Průvodce přidáním vlastnosti  
  
1.  V zobrazení tříd rozbalte větev mnohoúhelníku.  
  
2.  Klikněte pravým tlačítkem na IPolyCtl.  
  
3.  V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na **přidat vlastnost**.  
  
     Zobrazí se Průvodce přidáním vlastnosti.  
  
4.  V rozevíracím seznamu typy vlastností, vyberte `SHORT`.  
  
5.  Typ `Sides` jako **název vlastnosti.**  
  
6.  Klikněte na tlačítko **Dokončit** mohli dokončit přidávání člena vlastnost.  
  
 Přidáte-li vlastnost rozhraní, definuje MIDL (program, který se zkompiluje soubory .idl) `Get` metodu pro načtení jeho hodnotu a `Put` metodu pro nastavení novou hodnotu. Tyto metody jsou pojmenované předponou `put_` a `get_` název vlastnosti.  
  
 Průvodce přidáním vlastnosti přidá do souboru IDL nezbytné řádky. Přidává také `Get` a `Put` funkce prototypy v definici třídy v PolyCtl.h a přidá do PolyCtl.cpp implementaci prázdný. To můžete zkontrolovat otevřením PolyCtl.cpp a hledá funkce `get_Sides` a `put_Sides`.  
  
 I když Teď máte kostru funkce nastavit a načíst vlastnost, je místo, kam můžete ukládat. Vytvořte proměnnou pro ukládání vlastnosti a funkce se aktualizují odpovídajícím způsobem.  
  
#### <a name="to-create-a-variable-to-store-the-property-and-update-the-put-and-get-methods"></a>Chcete-li vytvořit proměnnou pro uložení vlastnosti a aktualizovat put a metodám get  
  
1.  V Průzkumníku řešení otevřete PolyCtl.h a přidejte následující řádek po definování `m_clrFillColor`:  
  
     [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]  
  
2.  Nastavit výchozí hodnotu `m_nSides`. Nastavte jako výchozí utvářejí trojúhelník přidáním řádku do konstruktoru v PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]  
  
3.  Implementace `Get` a `Put` metody. `get_Sides` a `put_Sides` deklarace funkce přidané do PolyCtl.h. Nahraďte kód v PolyCtl.cpp pro `get_Sides` a `put_Sides` následujícím kódem:  
  
     [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]  
  
 `get_Sides` Metoda vrací aktuální hodnotu `Sides` vlastnosti prostřednictvím `pVal` ukazatel. V `put_Sides` metody kód zajišťuje uživatele se nastaví `Sides` vlastnost přijatelnou hodnotu. Minimální hodnota musí být 3 a vzhledem k tomu, že pole bodů se použije pro každé straně, 100 je přiměřené limit pro maximální hodnotu.  
  
 Nyní máte vlastnost s názvem `Sides`. V dalším kroku se změní kreslení kód, který se použije.  
  
 [Zpátky ke kroku 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [na krok 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz](../atl/active-template-library-atl-tutorial.md)

