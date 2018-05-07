---
title: Chyba kompilátoru prostředků RW2002 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW2002
dev_langs:
- C++
helpviewer_keywords:
- RW2002
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb42298a7140439e3578281de60075f540b09175
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-error-rw2002"></a>Chyba kompilátoru prostředků RW2002
Při analýze  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  **Typ akcelerátoru vyžadovaný (ASCII nebo VIRTKEY)**  
  
     `type` Pole **AKCELERÁTORŮ** příkazu musí obsahovat buď ASCII nebo VIRTKEY hodnotu.  
  
2.  **V tabulce akcelerátorů byl očekáván začátek**  
  
     **Začít** okamžitě postupujte – klíčové slovo **AKCELERÁTORŮ** – klíčové slovo.  
  
3.  **V dialogovém okně byl očekáván začátek**  
  
     **Začít** okamžitě postupujte – klíčové slovo **dialogové okno** – klíčové slovo.  
  
4.  **V nabídce byl očekáván začátek**  
  
     **Začít** okamžitě postupujte – klíčové slovo **nabídky** – klíčové slovo.  
  
5.  **V RCData byl očekáván začátek**  
  
     **Začít** okamžitě postupujte – klíčové slovo **RCDATA** – klíčové slovo.  
  
6.  **BEGIN – klíčové slovo očekává v tabulce řetězců**  
  
     **Začít** okamžitě postupujte – klíčové slovo **STRINGTABLE** – klíčové slovo.  
  
7.  **nelze znovu použít řetězcové konstanty**  
  
     Používáte stejnou hodnotu dvakrát v **STRINGTABLE** příkaz. Ujistěte se, že nejsou kombinování překrývání desetinné hodnoty, šestnáctkové hodnoty. V každé ID **STRINGTABLE** musí být jedinečný. Pro maximální účinnost použijte souvislý konstanty, které začínají na více 16.  
  
8.  **Řízení znak mimo rozsah [^ A - ^ Z]**  
  
     Řídicí znak v **AKCELERÁTORŮ** příkaz je neplatný. Znak následující pomocí kurzoru (**^**) musí být v rozsahu A a Z, včetně.  
  
9. **není povolen prázdný nabídky**  
  
     **END** – klíčové slovo se nachází před všechny položky nabídky, jsou definovány v **nabídky** příkaz. Kompilátor prostředků nepovoluje prázdný nabídky. Zajistěte, aby všechny otevřené uvozovky, v rámci nemáte **nabídky** příkaz.  
  
10. **V dialogovém okně byl očekáván END**  
  
     **END** – klíčové slovo musí dojít na konci **dialogové okno** příkaz. Zajistěte, aby neexistují žádné otevřete uvozovky, ponecháno z předchozí příkaz.  
  
11. **V nabídce byl očekáván END**  
  
     **END** – klíčové slovo musí být na konci **nabídky** příkaz. Ujistěte se, máte všechny uvozovky, otevřete nebo pár neodpovídající **začít** a **END** příkazy.  
  
12. **Očekávaný čárkami v tabulce akcelerátorů**  
  
     Kompilátor prostředků vyžaduje čárka oddělující `event` a *idvalue* polí v **AKCELERÁTORŮ** příkaz.  
  
13. **Název třídy očekávané ovládacího prvku**  
  
     `class` Pole z **ovládací PRVEK** příkaz v **dialogové okno** příkaz musí mít jednu z následujících typů: tlačítko, COMBOBOX, upravit, LISTBOX, SCROLLBAR, statické, nebo definované uživatelem. Ujistěte se, že třída je napsán správně.  
  
14. **Byl očekáván název řez písma**  
  
     *Řez písma* pole možnosti písma ve **dialogové okno** příkaz musí být řetězec znaků ASCII, který je uzavřena v uvozovkách. Toto pole určuje název písma.  
  
15. **Očekávaná hodnota ID pro menuitem**  
  
     **Nabídky** příkaz musí obsahovat *menuID* pole, které určuje název nebo číslo, které identifikuje prostředek nabídky.  
  
16. **Řetězec očekávané nabídky**  
  
     Každý **MENUITEM** a **místní** příkaz musí obsahovat *text* pole, která je uzavřena v uvozovkách řetězec, který určuje název položky nabídky nebo automaticky otevírané okno nabídky. A **MENUITEM ODDĚLOVAČE** příkaz vyžaduje žádné řetězec v uvozovkách.  
  
17. **byla očekávána hodnota číselného příkaz**  
  
     Kompilátor prostředků očekával jednu číslici *idvalue* pole **AKCELERÁTORŮ** příkaz. Ujistěte se, že jste použili `#define` Konstanta zadejte hodnotu a že konstanta je napsán správně.  
  
18. **Očekávaný číselnou konstantu v tabulce řetězců**  
  
     Číselnou konstantu, definované v `#define` okamžitě prohlášení, postupujte **začít** – klíčové slovo v **STRINGTABLE** příkaz.  
  
19. **Očekávaný číselná velikost**  
  
     *Pointsize* pole možnosti písma ve **dialogové okno** příkaz musí být celočíselná hodnota velikost bodu.  
  
20. **Konstanta očekávané číselné dialogové okno**  
  
     A **dialogové okno** příkaz vyžaduje celočíselné hodnoty *x, y, šířka*, a *výška* pole. Ujistěte se, že tyto hodnoty jsou zahrnuty po **dialogové okno** – klíčové slovo a že nejsou záporné.  
  
21. **Očekávaný řetězec v STRINGTABLE**  
  
     Je očekáván řetězec po každém z nich *řetězců* hodnotu **STRINGTABLE** příkaz.  
  
22. **Očekávaný řetězec nebo konstantní akcelerátor – příkaz**  
  
     Kompilátor prostředků se nepodařilo určit, jaký typ klíče se nastavuje pro akcelerátor. `event` Pole **AKCELERÁTORŮ** příkaz může být neplatný.  
  
23. **byla očekávána číslo pro ID**  
  
     Byla očekávána počet `id` pole příkazu ovládací prvek v **dialogové okno** příkaz. Zajistěte, aby byla číslo nebo `#define` údajů pro ID ovládacího prvku.  
  
24. **Byl očekáván řetězec v uvozovkách ve třídě dialog**  
  
     `class` Pole možnosti třídy ve **dialogové okno** příkaz musí být celé číslo nebo řetězec, uzavřena v uvozovkách.  
  
25. **V dialogovém okně název je očekáván řetězec v uvozovkách**  
  
     `captiontext` Pole TITULKU možnosti ve **dialogové okno** příkaz musí být řetězec znaků ASCII, který je uzavřena v uvozovkách.  
  
26. **Soubor nebyl nalezen: název souboru**  
  
     Nebyl nalezen v souboru určeném v příkazovém řádku kompilátoru prostředků. Zkontrolujte, zda soubor byl přesunut do jiného adresáře a zda název souboru nebo cesta zadána správně. Prohledají se soubory pro použití **zahrnout** proměnné prostředí nebo nastavení Visual Workbench, pokud je k dispozici.  
  
27. **Názvy písma musí být řadové číslovky**  
  
     *Pointsize* pole v příkazu písma musí být celé číslo, není řetězec.  
  
28. **Neplatný akcelerátoru**  
  
     `event` Pole **AKCELERÁTORŮ** příkaz nebyl rozpoznán nebo byl více než dva znaky.  
  
29. **Neplatný akcelerátoru typu (ASCII nebo VIRTKEY)**  
  
     `type` Pole **AKCELERÁTORŮ** příkazu musí obsahovat buď ASCII nebo VIRTKEY hodnotu.  
  
30. **Neplatný řídicí znak**  
  
     Řídicí znak v **AKCELERÁTORŮ** příkaz je neplatný. Neplatný řídicí znak tvořený jedním písmenem (pouze) následující šipka nahoru (^).  
  
31. **Neplatný ovládací prvek typu**  
  
     Každý příkaz ovládacího prvku v **dialogové okno** příkaz musí být jeden z následujících: zaškrtávací políčko, COMBOBOX, řízení, CTEXT, DEFPUSHBUTTON, EDITTEXT, GROUPBOX, ikona, LISTBOX, LTEXT, PUSHBUTTON, RADIOBUTTON, RTEXT, SCROLLBAR. Zajistěte, aby tyto řídicí příkazy jsou správně zadané.  
  
32. **Neplatný typ**  
  
     Typ prostředku nebyl mezi typy definované v souboru odkazující na Windows.  
  
33. **Textový řetězec nebo pořadí očekává v ovládacím prvku**  
  
     *Text* pole z **řízení** příkaz v **dialogové okno** příkaz musí být textový řetězec nebo odkaz na pořadovém místě pro typ ovládacího prvku. Pokud pomocí pořadí, ujistěte se, že máte `#define` příkaz pro ovládací prvek.  
  
34. **Nesprávné závorky**  
  
     Zkontrolujte všechny otevřené závorky zavřeli **dialogové okno** příkaz.  
  
35. **Neočekávaná hodnota v RCData**  
  
     *Nezpracovaná data* hodnoty ve **RCDATA** příkaz musí být celá čísla nebo řetězce, oddělených čárkou. Ujistěte se, že jste vynechte čárkou nebo vynechte uvozovky kolem řetězec.  
  
36. **Podtyp neznámé nabídky**  
  
     *Definice položky* pole z **nabídky** příkaz může obsahovat pouze **MENUITEM** a **místní** příkazy.