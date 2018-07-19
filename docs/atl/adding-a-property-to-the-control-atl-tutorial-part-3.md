---
title: Přidání vlastnosti do ovládacího prvku (ATL – tutoriál, část 3) | Dokumentace Microsoftu
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
ms.openlocfilehash: 7cbfb0b22579aceb5cbee196e3c5eda3079c9304
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848714"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>Přidání vlastnosti do ovládacího prvku (ATL – tutoriál, část 3)
`IPolyCtl` je rozhraní, které obsahuje ovládacího prvku vlastní metody a vlastnosti a přidáte do jeho vlastnosti.  
  
### <a name="to-add-a-property-using-the-add-property-wizard"></a>Přidání vlastnosti pomocí Průvodce přidáním vlastnosti  
  
1.  V zobrazení tříd rozbalte větev mnohoúhelníku.  
  
2.  Klikněte pravým tlačítkem na IPolyCtl.  
  
3.  V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat vlastnost**.  
  
     Zobrazí se Průvodce přidáním vlastnosti.  
  
4.  V rozevíracím seznamu typy vlastností, vyberte `SHORT`.  
  
5.  Typ *strany* jako **název vlastnosti.**  
  
6.  Klikněte na tlačítko **Dokončit** mohli dokončit přidávání vlastnost.  
  
 Při přidání vlastnosti do rozhraní definuje MIDL (programu, který zkompiluje soubory .idl) `Get` metodu pro načtení jeho hodnotu a `Put` metodu pro nastavení novou hodnotu. Metody jsou pojmenovány předponou v podobě `put_` a `get_` název vlastnosti.  
  
 Průvodce přidáním vlastnosti přidá potřebné řádky do souboru IDL. Přidá také `Get` a `Put` funkční prototypy do definice třídy do souboru PolyCtl.h a přidá do PolyCtl.cpp prázdná implementace. Můžete zkontrolovat otevřením PolyCtl.cpp a hledáte funkce `get_Sides` a `put_Sides`.  
  
 I když Teď máte kostru funkce pro nastavení a načtení vlastnosti, potřebuje místo k uložení. Vytvoříte proměnnou pro uložení vlastnost a odpovídajícím způsobem aktualizace funkcí.  
  
#### <a name="to-create-a-variable-to-store-the-property-and-update-the-put-and-get-methods"></a>Vytvoření proměnné k ukládání vlastnost a aktualizovat put a metodám get  
  
1.  V Průzkumníku řešení otevřete souboru PolyCtl.h a přidejte následující řádek po definování `m_clrFillColor`:  
  
     [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]  
  
2.  Nastavit výchozí hodnotu `m_nSides`. Nastavit jako výchozí obrazce Trojúhelník konstruktoru v souboru PolyCtl.h přidejte řádek:  
  
     [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]  
  
3.  Implementace `Get` a `Put` metody. `get_Sides` a `put_Sides` deklarace funkce byly přidány do souboru PolyCtl.h. Nahraďte kód v PolyCtl.cpp pro `get_Sides` a `put_Sides` následujícím kódem:  
  
     [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]  
  
 `get_Sides` Metoda vrátí aktuální hodnotu `Sides` vlastnosti prostřednictvím `pVal` ukazatele. V `put_Sides` zajišťuje kód metodu, nastavení uživatele `Sides` vlastnost přijatelné hodnoty. Minimální hodnota musí být 3 a vzhledem k tomu, že pole body se použije pro každé straně, 100, je rozumné limit pro maximální hodnotu.  
  
 Teď mají vlastnost zvanou `Sides`. V dalším kroku změníte výkresu kód pro jeho použití.  
  
 [Zpátky ke kroku 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [ke kroku 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz](../atl/active-template-library-atl-tutorial.md)

