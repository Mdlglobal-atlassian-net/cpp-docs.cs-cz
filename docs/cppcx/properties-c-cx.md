---
title: Vlastnosti (C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 64c7bc56-3191-4cd5-bdf4-476d07d285d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f5cfe1bf4ae614bc892b4ea93d36fa44604029f1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764303"
---
# <a name="properties-ccx"></a>Vlastnosti (C + +/ CX)
Veřejné datové typy Windows Runtime vystavit jako vlastnosti. Klientský kód přistupuje k vlastnosti stejně jako veřejné datamember. Vlastnost interně, je implementovaný jako blok, který obsahuje metodu přístupového objektu get nebo metodu přístupového objektu set. Pomocí přístupových metod lze provádět další akce před nebo po načtení hodnoty, například může vyvolat událost nebo provádět kontroly ověřování.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je obsažen v soukromé proměnné – označované jako *záložní úložiště*– což je stejného typu jako vlastnost. Vlastnost může obsahovat přistupující objekt set, který přiřazuje hodnotu záložní úložiště, a přístupový objekt get, který načítá hodnoty ze záložního úložiště. Vlastnost je jen pro čtení v případě, že poskytuje pouze přístupový objekt get, jen pro zápis, pokud se poskytuje pouze přístupový objekt set a čtení/zápis (upravovat), pokud poskytuje přistupující objekty jak.  
  
 A *triviální* je vlastnost pro čtení a zápis, pro které kompilátor automaticky implementuje přístupové objekty a záložního úložiště. Nemáte přístup k implementaci kompilátor. Můžete však deklarovat vlastní vlastnost a explicitně deklarovat její přístupové objekty a záložního úložiště. V rámci přistupující objekt můžete provádět jakékoli logiky, která budete potřebovat, jako je například ověřování vstupu pro přistupující objekt set, výpočtu hodnoty z hodnoty vlastnosti, přístup k databázi nebo aktivaci události při změně vlastnosti.  
  
 Když C + +/ CX referenční třídy je vytvořena instance, jeho paměti je inicializována nulou před voláním konstruktoru; proto všechny vlastnosti jsou přiřazeny výchozí hodnotu nula nebo nullptr bodě deklarace.  
  
### <a name="examples"></a>Příklady  
 Následující příklad kódu ukazuje, jak deklarovat a přístup k vlastnosti. Vlastnost první `Name`, se označuje jako *triviální* vlastnost vzhledem k tomu, že kompilátor automaticky generuje `set` přístupový objekt, `get` přistupující objekt a záložního úložiště.  
  
 Druhá vlastnost `Doctor`, je vlastnost jen pro čtení, protože je určeno *vlastnost bloku* , který explicitně deklaruje pouze `get` přistupujícího objektu. Protože bloku vlastnost je teď deklarována, musíte explicitně deklarovat záložní úložiště; To znamená, privátní řetězec ^ proměnnou, `doctor_`. Vlastnost jen pro čtení obvykle pouze vrátí hodnotu záložního úložiště. Vlastní třídy můžete nastavit hodnotu záložní úložiště, obvykle v konstruktoru.  
  
 Vlastnost třetí `Quantity`, je vlastnost pro čtení i zápis, protože deklaruje vlastnost blok, který deklaruje i `set` přístupového objektu a `get` přistupujícího objektu.  
  
 `set` Přistupující objekt provádí test uživatelské platnosti na přiřazené hodnotě. A na rozdíl od jazyka C#, tady název *hodnotu* je identifikátor pro parametr v `set` přistupující objekt; není klíčové slovo. Pokud *hodnotu* není větší než nula, je vyvolána Platform::InvalidArgumentException. V opačném případě základní ukládání, `quantity_`, se aktualizuje s přiřazenou hodnotou.  
  
 Všimněte si, že vlastnost nejde inicializovat ve seznamu členů. Samozřejmě můžete inicializovat proměnné úložiště zálohování v seznamu členů.  
  
 [!code-cpp[cx_properties#01](../cppcx/codesnippet/CPP/cx_properties/class1.h#01)]  
  
## <a name="see-also"></a>Viz také  
 [Systém typů](../cppcx/type-system-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)