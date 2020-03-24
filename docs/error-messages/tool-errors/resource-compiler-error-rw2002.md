---
title: Chyba kompilátoru prostředků RW2002
ms.date: 11/04/2016
f1_keywords:
- RW2002
helpviewer_keywords:
- RW2002
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
ms.openlocfilehash: 9c5c2824778a679627bd3008276849890f43ac7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190687"
---
# <a name="resource-compiler-error-rw2002"></a>Chyba kompilátoru prostředků RW2002

Chyba analýzy

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. **Vyžaduje se typ akcelerátoru (ASCII nebo VIRTKEY).**

   Pole `type` v příkazu **akcelerátory** musí obsahovat hodnotu ASCII nebo VIRTKEY.

1. **V tabulce akcelerátorů byl očekáván začátek.**

   Klíčové slovo **Begin** musí následovat hned za klíčovým slovem **akcelerátory** .

1. **V dialogu se očekával začátek.**

   Klíčové slovo **Begin** musí následovat hned po klíčovém slově **dialog** .

1. **Nabídka BEGIN očekávala v nabídce**

   Klíčové slovo **Begin** musí následovat hned za klíčovým slovem **nabídky** .

1. **V RCData se očekává začátek.**

   Klíčové slovo **Begin** musí následovat hned za klíčovým slovem **RCDATA** .

1. **V tabulce řetězců bylo očekáváno klíčové slovo BEGIN**

   Klíčové slovo **Begin** musí ihned následovat po klíčovém slově **String** .

1. **Řetězcové konstanty nejde znovu použít.**

   V příkazu typu **String** se používá stejná hodnota dvakrát. Ujistěte se, že nemísíte překrývající se desítkové a hexadecimální hodnoty. Každé ID v **řetězcích řetězců** musí být jedinečné. Pro maximální efektivitu použijte souvislé konstanty, které začínají na násobcích 16.

1. **Řídicí znak je mimo rozsah [^ A-^ Z].**

   Řídicí znak v příkazu **akcelerátory** je neplatný. Znak následující po znaku stříšky ( **^** ) musí být mezi a a Z včetně.

1. **Prázdné nabídky nejsou povoleny**

   Klíčové slovo **End** se zobrazí před definováním položek nabídky v příkazu **nabídky** . Kompilátor prostředků nepovoluje prázdné nabídky. Ujistěte se, že v příkazu **nabídky** nejsou žádné otevřené uvozovky.

1. **KONEC očekáván v dialogovém okně**

   Klíčové slovo **End** se musí vyskytovat na konci příkazu **dialogového okna** . Zajistěte, aby z předchozího příkazu nezůstaly žádné otevřené uvozovky.

1. **KONEC očekáván v nabídce**

   Klíčové slovo **End** musí být uvedené na konci příkazu **nabídky** . Ujistěte se, že nemáte otevřené uvozovky nebo neshodující dvojici příkazů **Begin** a **End** .

1. **Očekávaná čárka v tabulce akcelerátorů**

   Kompilátor prostředků vyžaduje čárku mezi poli `event` a *idValue* v příkazu **akcelerátory** .

1. **Očekával se název třídy ovládacího prvku.**

   Pole `class` příkazu **Control** v příkazu **dialogového okna** musí být jeden z následujících typů: tlačítko, pole se seznamem, úpravy, seznam, posuvník, statická nebo uživatelsky definovaná. Ujistěte se, že je třída správně napsaná.

1. **Očekával se název vzhledu písma.**

   Pole *řezu* v možnosti písmo v příkazu **dialogového okna** musí být řetězec znaků ASCII uzavřený v dvojitých uvozovkách. Toto pole určuje název písma.

1. **Očekávaná hodnota ID pro MenuItem**

   Příkaz **nabídky** musí obsahovat pole *MenuID* , které určuje název nebo číslo identifikující prostředek nabídky.

1. **Očekávaný řetězec nabídky**

   Každý příkaz **MenuItem** a **Překryvné okno** musí obsahovat *textové* pole, což je řetězec uzavřený v dvojitých uvozovkách, který určuje název položky nabídky nebo místní nabídky. Příkaz **oddělovače položky MenuItem** nevyžaduje žádný řetězec v uvozovkách.

1. **Očekávaná hodnota číselného příkazu**

   Kompilátor prostředků očekával v příkazu **akcelerátory** číselné pole *idValue* . Ujistěte se, že jste použili `#define` konstanty k zadání hodnoty a zda je konstanta zadána správně.

1. **Očekávaná číselná konstanta v tabulce řetězců**

   Číselná konstanta definovaná v příkazu `#define` musí hned následovat po klíčovém slovu **Begin** v příkazu typu **String** .

1. **Očekávaná velikost číselného bodu**

   Pole *Pointsize* možnosti Font v příkazu **dialogového okna** musí být hodnota velikosti celého čísla.

1. **Očekávaná konstanta číselných dialogových oken**

   Příkaz **dialogového okna** vyžaduje celočíselné hodnoty pro pole *x, y, Width*a *Height* . Ujistěte se, že tyto hodnoty jsou zahrnuty po klíčovém slově **dialogového okna** a že nejsou záporné.

1. **V řetězci STRING byl očekáván řetězec.**

   Za každou hodnotu *stringid* v příkazu typu **String** se očekává řetězec.

1. **Očekával se řetězec nebo příkaz pro konstantní akcelerátor.**

   Kompilátor prostředků nebyl schopný určit, jaký druh klíče se má pro akcelerátor nastavovat. Pole `event` v příkazu **akcelerátory** mohou být neplatné.

1. **Očekávalo se číslo ID.**

   Očekává se číslo pro pole `id` příkazu ovládacího prvku v příkazu **dialogového okna** . Ujistěte se, že máte příkaz číslo nebo `#define` pro ID ovládacího prvku.

1. **Očekává se řetězec v uvozovkách ve třídě dialogového okna.**

   Pole `class` v možnosti třídy v příkazu **dialogového okna** musí být celé číslo nebo řetězec uzavřený do dvojitých uvozovek.

1. **V názvu dialogového okna je očekáván řetězec v uvozovkách.**

   Pole `captiontext` možnosti CAPTION v příkazu **dialog** musí být řetězec znaků ASCII uzavřený v dvojitých uvozovkách.

1. **Soubor nebyl nalezen: název souboru**

   Soubor zadaný v příkazovém řádku kompilátoru prostředků se nenašel. Zkontrolujte, zda byl soubor přesunut do jiného adresáře a zda je správně zadán název souboru nebo cesta. Soubory jsou prohledány pomocí proměnné prostředí **include** nebo nastavení sady Visual Studio, jsou-li k dispozici.

1. **Názvy písem musí být anglické a anglické.**

   Pole *Pointsize* v příkazu Font musí být celé číslo, nikoli řetězec.

1. **Neplatný akcelerátor**

   Pole `event` v příkazu **akcelerátory** nebylo rozpoznáno nebo bylo delší než dva znaky.

1. **Neplatný typ akcelerátoru (ASCII nebo VIRTKEY)**

   Pole `type` v příkazu **akcelerátory** musí obsahovat hodnotu ASCII nebo VIRTKEY.

1. **Neplatný řídicí znak**

   Řídicí znak v příkazu **akcelerátory** je neplatný. Platný řídicí znak se skládá z jednoho písmena (pouze) za blikajícím kurzorem (^).

1. **Neplatný typ ovládacího prvku**

   Každý příkaz ovládacího prvku v příkazu **dialogového okna** musí být jedna z následujících: CheckBox, ComboBox, Control, CTEXT, DEFPUSHBUTTON, EditText, skupinový, Icon, ListBox, LTEXT, (pushbutton), RadioButton, RText, SCROLLBAR. Ujistěte se, že jsou tyto příkazy ovládacích prvků zadány správně.

1. **Neplatný typ**

   Typ prostředku nebyl mezi typy definovanými v souboru WINDOWS. h.

1. **V ovládacím prvku byl očekáván textový řetězec nebo pořadové číslo.**

   *Textové* pole příkazu **ovládacího prvku** v příkazu **dialogového okna** musí být textový řetězec nebo odkaz na pořadové číslo typu ovládacího prvku. Pokud používáte ordinální číslo, ujistěte se, že máte příkaz `#define` pro ovládací prvek.

1. **Neshoda závorek**

   Ujistěte se, že jste v příkazu **dialogu** zavřeli každou levou závorku.

1. **Neočekávaná hodnota v RCData**

   Hodnoty *nezpracovaných dat* v příkazu **RCDATA** musí být celá čísla nebo řetězce, z nichž každá je oddělena čárkou. Ujistěte se, že jste nenechali čárku nebo jste ponechali znak uvozovek kolem řetězce.

1. **Neznámý podtyp nabídky**

   Pole *definice položky* příkazu **nabídky** může obsahovat pouze příkazy **MenuItem** a **Překryvné okno** .
