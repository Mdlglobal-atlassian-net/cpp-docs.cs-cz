---
title: Chyba kompilátoru prostředků RW2002 | Dokumentace Microsoftu
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
ms.openlocfilehash: 50d2993c4f8e7053867aa0757e90a0f7f1b1190c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112899"
---
# <a name="resource-compiler-error-rw2002"></a>Chyba kompilátoru prostředků RW2002

Chyba parsování

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. **Typ akcelerátoru povinná (ASCII nebo VIRTKEY)**

     `type` Pole **AKCELERÁTORY** příkazu musí obsahovat hodnotu ASCII nebo VIRTKEY.

1. **ZAČÁTEK očekávání v tabulce akcelerátorů**

     **Začít** – klíčové slovo musí následovat bezprostředně **AKCELERÁTORY** – klíčové slovo.

1. **V dialogovém okně očekáván začátek**

     **Začít** – klíčové slovo musí následovat bezprostředně **dialogové okno** – klíčové slovo.

1. **V nabídce byl očekáván začátek**

     **Začít** – klíčové slovo musí následovat bezprostředně **nabídky** – klíčové slovo.

1. **Byl očekáván v RCData BEGIN**

     **Začít** – klíčové slovo musí následovat bezprostředně **RCDATA** – klíčové slovo.

1. **Byl očekáván v tabulce řetězců – klíčové slovo BEGIN**

     **Začít** – klíčové slovo musí následovat bezprostředně **STRINGTABLE** – klíčové slovo.

1. **nelze znovu použít řetězcové konstanty**

     Používáte dvakrát na stejnou hodnotu **STRINGTABLE** příkazu. Ujistěte se, že nejsou kombinování překrývající se desetinných míst a šestnáctkové hodnoty. V každé ID **STRINGTABLE** musí být jedinečný. Maximální účinnost použijte souvislých konstanty, které začínají na násobkem 16.

1. **Řídící znaku mimo rozsah [^ A - ^ Z]**

     Řídicí znak v **AKCELERÁTORY** příkaz je neplatný. Znak po znaku stříšky (**^**) musí být v rozmezí A a vykreslování (včetně).

9. **prázdné nabídky není povolená.**

     **END** – klíčové slovo se nachází před všechny položky nabídky jsou definovány v **nabídky** příkazu. Nástroj Resource Compiler neumožňuje prázdné nabídky. Ujistěte se, že nemáte žádné otevřené uvozovek v rámci **nabídky** příkazu.

10. **END očekává v dialogovém okně**

     **END** – klíčové slovo se musí vyskytovat na konci **dialogové okno** příkazu. Ujistěte se, že neexistují žádné otevřené nabídky vlevo od předchozího příkazu.

11. **END očekává v nabídce**

     **END** – klíčové slovo musí být na konci **nabídky** příkazu. Ujistěte se, že máte všechny otevřené uvozovky nebo neshoda dvojice **začít** a **END** příkazy.

12. **Očekávaný čárka v tabulce akcelerátorů**

     Nástroj Resource Compiler vyžaduje čárkou `event` a *idvalue* pole v **AKCELERÁTORY** příkazu.

13. **Název třídy očekávané ovládacího prvku**

     `class` Pole **ovládací PRVEK** příkaz v **dialogové okno** příkazu musí být jedna z následujících typů: tlačítko, pole se SEZNAMEM, úpravy, LISTBOX, POSUVNÍK, STATICKÝ, nebo uživatelem definovaný. Ujistěte se, že třída je napsán správně.

14. **Očekával se název písma pro rozpoznávání tváře**

     *Řez písma* pole možnosti písma ve **dialogové okno** příkazu musí být řetězec znaků ASCII, který je uzavřen do dvojitých uvozovek. Toto pole určuje název písma.

15. **Očekávaná hodnota ID pro položku nabídky**

     **Nabídky** musí obsahovat prohlášení *menuID* pole, který určuje název nebo číslo, která identifikuje prostředek nabídky.

16. **Řetězec očekávaný nabídky**

     Každý **MENUITEM** a **automaticky otevírané okno** musí obsahovat příkaz *text* pole, který je uzavřen do dvojitých uvozovek řetězec, který určuje název položky nabídky nebo automaticky otevírané okno nabídka. A **MENUITEM ODDĚLOVAČ** příkaz vyžaduje žádný řetězec v uvozovkách.

17. **byl očekáván příkaz číselnou hodnotu**

     Nástroj Resource Compiler očekávala číselnou *idvalue* pole **AKCELERÁTORY** příkazu. Ujistěte se, že jste použili `#define` – konstanta určíte hodnotu a konstanty není napsaný špatně.

18. **Byl očekáván číselnou konstantu v tabulce řetězců**

     Číselné konstanty definované v `#define` příkaz, musí následovat bezprostředně **začít** – klíčové slovo v **STRINGTABLE** příkazu.

19. **Byl očekáván číselný velikost**

     *Pointsize* pole možnosti písma ve **dialogové okno** příkazu musí být celočíselná hodnota velikosti bodu.

20. **byl očekáván číselný dialogové okno – konstanta**

     A **dialogové okno** příkazu vyžaduje celočíselné hodnoty *x, y, šířka*, a *výška* pole. Ujistěte se, že tyto hodnoty jsou zahrnuty po **dialogové okno** – klíčové slovo a že nejsou záporné.

21. **Očekávaný řetězec v STRINGTABLE**

     Očekává se řetězec po každém z nich *stringid* hodnotu **STRINGTABLE** příkazu.

22. **Očekával se řetězcový nebo konstantní akcelerátor – příkaz**

     Nástroj Resource Compiler nebyl schopen určit, jaký typ klíče se nastavuje pro akcelerátor. `event` Pole **AKCELERÁTORY** příkaz může být neplatný.

23. **Očekává se číslo ID**

     Očekává se číslo pro `id` pole v příkazu ovládacího prvku **dialogové okno** příkaz. Ujistěte se, že máte více nebo `#define` příkazu pro ID ovládacího prvku.

24. **Očekává se řetězec v uvozovkách ve třídě dialog**

     `class` Možnost třídy v poli **dialogové okno** příkazu musí být celé číslo nebo řetězec v dvojitých uvozovkách.

25. **Očekává se řetězec v uvozovkách v název dialogového okna**

     `captiontext` Pole možnosti TITULKŮ ve **dialogové okno** příkazu musí být řetězec znaků ASCII, který je uzavřen do dvojitých uvozovek.

26. **Soubor nebyl nalezen: název souboru**

     Nebyl nalezen zadaný soubor na příkazovém řádku pro kompilátor prostředků. Zkontrolujte, zda soubor byl přesunut do jiného adresáře a určuje, zda název souboru nebo cesta zadána správně. Soubory se vyhledávají pomocí **zahrnout** proměnné prostředí nebo nastavení Visual aplikace Workbench, pokud je k dispozici.

27. **Názvy musí být řadové číslovky**

     *Pointsize* pole v příkazu písma musí být celé číslo, není řetězec.

28. **Neplatný akcelerátoru**

     `event` Pole **AKCELERÁTORY** příkaz nebyl rozpoznán nebo byl více než dva znaky.

29. **Typ akcelerátoru neplatný (ASCII nebo VIRTKEY)**

     `type` Pole **AKCELERÁTORY** příkazu musí obsahovat hodnotu ASCII nebo VIRTKEY.

30. **Neplatný řídicí znak**

     Řídicí znak v **AKCELERÁTORY** příkaz je neplatný. Neplatný řídicí znak se skládá z jednoho písmeno (pouze) poté, co stříšky (^).

31. **Neplatný ovládací prvek typu**

     Každý příkaz ovládacího prvku v **dialogové okno** příkazu musí být jedna z následujících akcí: zaškrtávací políčko, pole se SEZNAMEM, ovládací PRVEK, CTEXT, DEFPUSHBUTTON, EDITTEXT, GROUPBOX, ikony, LISTBOX, LTEXT, PUSHBUTTON, ovládacího prvku RADIOBUTTON, RTEXT, POSUVNÍK. Ujistěte se, že tyto řídicí příkazy jsou zadány správně.

32. **Neplatný typ**

     Typ prostředku nebyl mezi typy definované v souboru WINDOWS.h.

33. **Textový řetězec nebo řádu očekávání v ovládacím prvku**

     *Text* pole **ovládací PRVEK** příkaz v **dialogové okno** příkazu musí být textový řetězec nebo odkaz na pořadovém místě pro typ ovládacího prvku. Pokud pomocí ordinální číslo, ujistěte se, že máte `#define` příkaz pro ovládací prvek.

34. **Závorky**

     Ujistěte se, že každý levou (otevírací) byly uzavřeny **dialogové okno** příkazu.

35. **Neočekávaná hodnota v RCData**

     *Nezpracovaná data* hodnoty v **RCDATA** příkaz musí být celá čísla nebo řetězce, každé oddělené čárkou. Ujistěte se, že jste nepřešly vynechte čárku nebo vynechte uvozovky kolem řetězec.

36. **Nabídka Neznámý podtyp**

     *Definice položky* pole **nabídky** příkaz může obsahovat pouze **MENUITEM** a **automaticky otevírané okno** příkazy.