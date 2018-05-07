---
title: Vlastnosti (C + +/ CX) | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 64c7bc56-3191-4cd5-bdf4-476d07d285d5
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6393b5e5849ab2198fa8d084c2c1d15838c69bdd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="properties-ccx"></a>Vlastnosti (C + +/ CX)
Typy prostředí Windows Runtime vystavit veřejná data jako vlastnosti. Kód klienta přistupuje k vlastnosti jako veřejné datamember. Vlastnost interně je implementovaný jako blok, který obsahuje metodu přistupující objekt get, metodu přistupující objekt set nebo obojí. Pomocí metody přístupových objektů lze provádět další akce před nebo po můžete načíst hodnotu, například může provést událost nebo provádí kontroly platnosti.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je obsažena v soukromé proměnné – označuje jako *záložnímu úložišti*– což je totéž jako vlastnost. Vlastnost může obsahovat přistupujícím objektem set, který přiřazuje hodnotu k záložnímu úložišti, a přistupující objekt get, který načte hodnotu záložnímu úložišti. Vlastnost je určeno jen pro čtení, pokud se poskytuje pouze přistupující, jen pro zápis, pokud se poskytuje pouze přistupující objekt set a pro čtení a zápis (upravitelnými), pokud poskytuje i přistupující objekty.  
  
 A *trivial* je pro čtení a zápis vlastnost, pro které kompilátor automaticky implementuje přístupové objekty a záložnímu úložišti. Nemáte přístup k implementaci do kompilátoru. Můžete však deklarovat vlastní vlastnost a explicitně deklarovat jeho přístupové objekty a záložnímu úložišti. V rámci přistupující objekt můžete provést jakékoli logiky, která budete potřebovat, jako jsou ověřování vstupu pro přistupující objekt set, výpočtu hodnoty z hodnoty vlastnosti, přístup k databázi nebo aktivuje událost při změně vlastnosti.  
  
 Když C + +/ CX ref třída je vytvořena instance, jeho paměti je nula inicializovat před jeho konstruktoru nazývá; proto všechny vlastnosti přiřazené výchozí hodnotu nula nebo nullptr v místě deklarace.  
  
### <a name="examples"></a>Příklady  
 Následující příklad kódu ukazuje, jak deklarace a přístup k vlastnosti. Vlastnost první `Name`, se označuje jako *trivial* vlastnost protože kompilátor automaticky generuje `set` přistupujícího objektu, `get` přistupujícího objektu a záložnímu úložišti.  
  
 Druhou vlastností `Doctor`, je vlastnost jen pro čtení, protože určuje *vlastnost bloku* který explicitně deklaruje pouze `get` přistupujícího objektu. Protože je deklarovaná vlastnost bloku, je potřeba explicitně deklarovat záložnímu úložišti; To znamená, privátní řetězec ^ proměnnou, `doctor_`. Vlastnosti jen pro čtení obvykle právě vrací hodnotu záložnímu úložišti. Pouze vlastní třídy můžete nastavit hodnotu úložiště zálohování, obvykle v konstruktoru.  
  
 Vlastnost třetí `Quantity`, je vlastnost pro čtení a zápis, protože deklaruje vlastnost blok, který deklaruje i `set` přistupujícího objektu a `get` přistupujícího objektu.  
  
 `set` Přistupujícího objektu provádí test uživatelem definované platnosti na základě přiřazené hodnoty. Na rozdíl od C#, zde název *hodnotu* je právě identifikátor pro parametr v `set` přistupující objekt; není klíčové slovo. Pokud *hodnota* není větší než nula, je vyvolána Platform::InvalidArgumentException. Základní, jinak hodnota uložit, `quantity_`, je aktualizován s přiřazenou hodnotou.  
  
 Všimněte si, že vlastnost nelze inicializovat, v seznamu členů. Samozřejmě můžete inicializovat proměnné úložiště zálohování v seznamu členů.  
  
 [!code-cpp[cx_properties#01](../cppcx/codesnippet/CPP/cx_properties/class1.h#01)]  
  
## <a name="see-also"></a>Viz také  
 [Systém typů](../cppcx/type-system-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)