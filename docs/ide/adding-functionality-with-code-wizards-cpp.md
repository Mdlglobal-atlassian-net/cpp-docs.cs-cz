---
title: Přidání funkce pomocí Průvodců kódem (C++)
ms.date: 05/14/2019
helpviewer_keywords:
- code wizards [C++]
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
ms.openlocfilehash: ab0bf802221bcf3f93469f27f29f86c95877a407
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365336"
---
# <a name="adding-functionality-with-code-wizards-c"></a>Přidání funkce pomocí Průvodců kódem (C++)

Po vytvoření projektu budete chtít změnit nebo přidat k jeho funkci. Mezi tyto úkoly patří vytváření nových tříd, přidávání nových členských funkcí a proměnných a přidávání metod a vlastností automatizace. Průvodci kódem jsou navrženy tak, aby vám umožní dělat všechny tyto věci.

> [!NOTE]
> Následující zřídka používané kód průvodců jsou odebrány v sadě Visual Studio 2019. Obecná podpora knihovny ATL a knihovny MFC není ovlivněna odebráním těchto průvodců. Ukázkový kód pro tyto technologie je archivován v Microsoft Docs a v úložišti GitHub VCSamples.

- Průvodce komponentami ATL COM+ 1.0
- Průvodce součástí Aktivní serverové stránky serveru ATL
- Průvodce zprostředkovatelem ATL OLE DB
- Průvodce stránkou vlastností ATL
- Průvodce příjemcem ATL OLE DB
- Příjemce rozhraní MFC ODBC
- Třída MFC z ovládacího prvku ActiveX
- Třída MFC z typu Lib.

> [!NOTE]
> Můžete do nich přidat obslužné rutiny zpráv a mapovat zprávy a přepsat virtuální funkce knihovny MFC pomocí [Průvodce třídami knihovny MFC](../mfc/reference/mfc-class-wizard.md).

## <a name="accessing-c-code-wizards"></a>Přístup k Průvodcům kódem jazyka C++

Existují tři umístění, kde můžete přistupovat k průvodcům kódu jazyka C++:

- V nabídce **Projekt** umožňuje příkaz **Přidat novou položku** `Add New Item` vyvolat dialogové okno, které vám pomůže přidat do projektu nové soubory. Příkaz **Přidat třídu** zobrazí dialogové okno [Přidat třídu,](../ide/add-class-dialog-box.md) které zase otevře průvodce pro každý typ třídy, který můžete přidat do projektu. Pro třídy knihovny MFC použijte [Průvodce třídou knihovny MFC](../mfc/reference/mfc-class-wizard.md). Příkaz **Přidat zdroj** zobrazí dialogové okno Přidat [zdroj,](../windows/add-resource-dialog-box.md) ze kterého můžete vytvořit nebo vybrat zdroj, který chcete přidat do projektu.

   Pokud zvýrazníte třídu nebo rozhraní v projektu v zobrazení tříd, nabídka **Projekt** také zobrazí následující příkazy:

  - **Implementovat rozhraní** (pouze z kontrolní třídy)

  - **Přidat funkci**

  - **Přidat proměnnou**

  - **Přidat spojovací bod** (pouze třída ATL)

  - **Přidat metodu** (pouze z rozhraní)

  - **Přidat vlastnost** (pouze z rozhraní)

  - **Přidat událost** (pouze z kontrolní třídy)

- V **Průzkumníku řešení**klepnete pravým tlačítkem myši na libovolnou složku a klepnutím na tlačítko **Přidat** z místní nabídky můžete přidat nové nebo existující soubory, další složky, položky, třídy, zdroje a webové odkazy na projekt.

- V [okně Zobrazení třídy](/visualstudio/ide/viewing-the-structure-of-code)klepnete pravým tlačítkem myši na příslušný uzel a klepnutím na tlačítko **Přidat** z místní nabídky můžete do projektu přidat funkce, proměnné, třídy, vlastnosti, metody, události, rozhraní, spojovací body nebo jiný kód.

   > [!NOTE]
   > Visual Studio neposkytuje průvodce pro přidání rozhraní do projektu. Můžete přidat rozhraní do projektu knihovny ATL nebo [přidání podpory knihovny ATL do projektu knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) přidáním jednoduchého objektu pomocí [Průvodce jednoduchým objektem knihovny ATL](../atl/reference/atl-simple-object-wizard.md). Případně otevřete soubor .idl projektu a vytvořte rozhraní zadáním:

    ```IDL
    interface IMyInterface {
    };
    ```

   Další informace naleznete [v tématu Implementace rozhraní](../ide/implementing-an-interface-visual-cpp.md) a přidání objektů a [ovládacích prvků do projektu knihovny ATL.](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)

   |Průvodce přístupovým kódem od|Popis|
   |-----------------------------|-----------------|
   |Přidat novou položku|Průvodci přidáním kódu nové položky přidají do projektu zdrojové soubory. V případě potřeby jsou vytvořeny další adresáře, které obsahují soubory, kde modul sestavení projektu očekává, že je najde. Mezi průvodce kódu, kteří jsou k dispozici na ikoně Přidat položku, patří:<br /><br />- Přidejte zdrojové soubory C++ (.cpp, .h, .idl, .rc, .srf, .def, .rgs).<br />- Přidat webové vývojové soubory (.html, .asp, .css, .xml).<br />- Přidejte utility a resource files (.bmp, .cur, .ico, .rct, .sql, .txt).<br /><br />Tito průvodci kódem obvykle nežádají o žádné informace, ale přidají soubor do vývojového stromu. Soubor můžete přejmenovat v okně vlastností.|
   |Průzkumník řešení|Průvodci kódem, kteří jsou k dispozici v Průzkumníku řešení, závisí na tom, kde je fokus kurzoru, když klepnete pravým tlačítkem myši na položku. Pokud **se** možnost Přidat nezobrazí, když kliknete pravým tlačítkem myši na položku, přesuňte kurzor o jednu úroveň nahoru ve vývojovém stromu a akci opakujte. Průvodci kódem vždy umístí další kód na příslušné místo ve vývojovém stromu, bez ohledu na to, kde je kurzor. Průvodci kódu, kteří jsou k dispozici v Průzkumníku řešení, zahrnují:<br /><br />- Přidat třídu (otevře dialogové okno **Přidat třídu** obsahující nové průvodce kódem).<br />- Přidat zdroj (nový, import nebo vlastní).<br />- Přidat webový odkaz.|
   |zobrazení tříd|Průvodci kódem, kteří jsou k dispozici v zobrazení třídy, závisí na tom, kde je zaměření kurzoru, když klepnete pravým tlačítkem myši na položku. Pokud se možnost **Přidat** nezobrazí, když kliknete pravým tlačítkem myši na položku, přesuňte kurzor o jednu úroveň nahoru ve stromu tříd a akci opakujte. Průvodci kódem vždy umístí další kód na příslušné místo ve vývojovém stromu, bez ohledu na to, kde je kurzor. Průvodci kódu, kteří jsou k dispozici v zobrazení tříd, zahrnují:<br /><br />- [Přidat člennou funkci](../ide/adding-a-member-function-visual-cpp.md).<br />- [Přidat člennou proměnnou](../ide/adding-a-member-variable-visual-cpp.md).<br />- [Přidat třídu](../ide/adding-a-class-visual-cpp.md).<br />- [Implementovat rozhraní](../ide/implement-interface-wizard.md) (pouze z kontrolní třídy)<br />- [Přidat spojovací bod](../ide/implement-connection-point-wizard.md) (pouze třída ATL)<br />- [Přidat metodu](../ide/add-method-wizard.md) (pouze z rozhraní)<br />- [Přidat vlastnost](../ide/names-add-property-wizard.md) (pouze z rozhraní)<br />- [Přidat událost](../ide/add-event-wizard.md) (pouze z kontrolní třídy)<br /><br />Výběr Přidat třídu otevře dialogové okno **Přidat třídu,** které vám umožní přístup ke všem novým průvodcům kódu přidat třídu.|

## <a name="see-also"></a>Viz také

[Přepsání virtuální funkce](../ide/overriding-a-virtual-function-visual-cpp.md)<br>
[Navigace v základu kódu Jazyka C++ v sadě Visual Studio](../ide/navigate-code-cpp.md)<br>
[Typy projektů Jazyka C++ v sadě Visual Studio](../build/reference/visual-cpp-project-types.md)<br>
[Typy souborů vytvořené pro projekty jazyka Visual Studio C++](../build/reference/file-types-created-for-visual-cpp-projects.md)
