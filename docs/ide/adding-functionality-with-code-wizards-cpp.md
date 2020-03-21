---
title: Přidání funkcí pomocí průvodců kódemC++()
ms.date: 05/14/2019
helpviewer_keywords:
- code wizards [C++]
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
ms.openlocfilehash: cb77b2ce74f962df0a4c7472b037cb7a73effc2d
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077700"
---
# <a name="adding-functionality-with-code-wizards-c"></a>Přidání funkcí pomocí průvodců kódemC++()

Po vytvoření projektu budete chtít změnit nebo přidat do funkce tohoto projektu. Mezi takové úlohy patří vytváření nových tříd, přidávání nových členských funkcí a proměnných a přidání metod a vlastností automatizace. Průvodci kódem jsou navrženi tak, aby umožňovala provádět všechny tyto akce.

> [!NOTE]
> Následující zřídka používané průvodce kódem jsou v aplikaci Visual Studio 2019 odebrány. Obecná podpora pro ATL a MFC není ovlivněna odebráním těchto průvodců. Vzorový kód pro tyto technologie je archivován na Microsoft Docs a úložišti GitHubu VCSamples.

- Průvodce komponentami ATL COM+ 1.0
- Průvodce komponentami ATL Active Server Pages
- Průvodce poskytovatelem OLE DB ATL
- Průvodce stránkou vlastností ATL
- Průvodce příjemcem OLE DB ATL
- Příjemce knihovny MFC rozhraní ODBC
- Třída MFC z ovládacího prvku ActiveX
- Třída MFC z knihovny typů.

> [!NOTE]
>  Můžete přidat obslužné rutiny zpráv a mapovat do nich zprávy a přepsat virtuální funkce knihovny MFC pomocí [Průvodce třídou MFC](../mfc/reference/mfc-class-wizard.md).

## <a name="accessing-c-code-wizards"></a>Přístup C++ k průvodcům kódu

Existují tři umístění, kde můžete získat přístup C++ k průvodcům kódu:

- V nabídce **projekt** umožňuje příkaz **Přidat novou položku** vyvolat dialogové okno `Add New Item`, které vám pomůže přidat do projektu nové soubory. Příkaz **Přidat třídu** zobrazí dialogové okno [Přidat třídu](../ide/add-class-dialog-box.md) , které v nástroji otevře Průvodce pro každý typ třídy, který můžete přidat do projektu. Pro třídy knihovny MFC použijte [Průvodce třídou MFC](../mfc/reference/mfc-class-wizard.md). V příkazu **Přidat prostředek** se zobrazí dialogové okno [Přidat prostředek](../windows/add-resource-dialog-box.md) , ve kterém můžete vytvořit nebo vybrat prostředek, který chcete přidat do projektu.

   Pokud v Zobrazení tříd zvýrazníte třídu nebo rozhraní v projektu, v nabídce **projekt** se zobrazí také následující příkazy:

   - **Implementovat rozhraní** (jenom z třídy ovládacího prvku)

   - **Přidat funkci**

   - **Přidat proměnnou**

   - **Přidat bod připojení** (pouze třída ATL)

   - **Add – metoda** (jenom z rozhraní)

   - **Přidat vlastnost** (jenom z rozhraní)

   - **Přidat událost** (pouze z třídy ovládacího prvku)

- V **Průzkumník řešení**klikněte pravým tlačítkem myši na libovolnou složku a kliknutím na tlačítko **Přidat** z místní nabídky můžete přidat nové nebo existující soubory, další složky, položky, třídy, prostředky a webové odkazy na projekt.

- V [okně zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code)klikněte pravým tlačítkem myši na příslušný uzel a kliknutím na tlačítko **Přidat** z místní nabídky můžete do projektu přidat funkce, proměnné, třídy, vlastnosti, metody, události, rozhraní, spojovací body nebo jiný kód.

   > [!NOTE]
   > Visual Studio neposkytuje průvodce pro přidání rozhraní do projektu. Můžete přidat rozhraní do projektu ATL nebo přidat [podporu knihovny ATL do projektu knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) přidáním jednoduchého objektu pomocí [Průvodce jednoduchým objektem ATL](../atl/reference/atl-simple-object-wizard.md). Alternativně otevřete soubor. idl projektu a vytvořte rozhraní zadáním:

    ```IDL
    interface IMyInterface {
    };
    ```

   Další informace naleznete v tématu [implementace rozhraní](../ide/implementing-an-interface-visual-cpp.md) a [Přidání objektů a ovládacích prvků do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) .

   |Průvodce kódem pro přístup z|Popis|
   |-----------------------------|-----------------|
   |Přidat novou položku|Průvodce přidáním nového kódu položky přidá zdrojové soubory do projektu. V případě potřeby jsou vytvořeny další adresáře, aby obsahovaly soubory, které modul pro sestavení projektu očekává, že je najde. Průvodci kódem dostupný z ikony Přidat položku zahrnují:<br /><br />-Přidat C++ zdrojové soubory (. cpp,. h,. idl,. RC,. SRF,. def,. rgs).<br />-Přidat webové vývojové soubory (. html,. ASP,. CSS,. XML).<br />– Přidejte soubory nástrojů a prostředků (. bmp,. měna,. ico,. RCT,. SQL,. txt).<br /><br />Tato průvodce kódem obecně nežádá o žádné informace, ale přidá soubor do stromu vývoje. Tento soubor můžete přejmenovat v okně vlastností.|
   |Průzkumník řešení|Průvodci kódem dostupnými z Průzkumník řešení závisí na tom, kde se fokus kurzoru nachází po kliknutí pravým tlačítkem myši na položku. Pokud se možnost **Přidat** nezobrazí, když kliknete pravým tlačítkem myši na položku, přesuňte kurzor o jednu úroveň výš ve vývojovém stromu a zkuste to znovu. Průvodce kódem bude vždy umístit další kód do příslušného místa ve vývojovém stromu, bez ohledu na to, kde je kurzor. Průvodci kódem dostupný z Průzkumník řešení zahrnují:<br /><br />-Přidat třídu (otevře se dialogové okno **Přidat třídu** obsahující nové průvodce kódem).<br />-Přidat prostředek (nový, import nebo vlastní).<br />-Přidat webový odkaz.|
   |zobrazení tříd|Průvodci kódem dostupnými z Zobrazení tříd závisí na tom, kde se fokus kurzoru zobrazí po kliknutí pravým tlačítkem myši na položku. Pokud se možnost **Přidat** nezobrazí, když kliknete pravým tlačítkem myši na položku, přesuňte kurzor o jednu úroveň výš ve stromu tříd a akci opakujte. Průvodce kódem bude vždy umístit další kód do příslušného místa ve vývojovém stromu, bez ohledu na to, kde je kurzor. Průvodci kódem dostupný z Zobrazení tříd zahrnují:<br /><br />- [Přidat členskou funkci](../ide/adding-a-member-function-visual-cpp.md).<br />- [Přidat členskou proměnnou](../ide/adding-a-member-variable-visual-cpp.md).<br />- [Přidat třídu](../ide/adding-a-class-visual-cpp.md).<br />- [implementovat rozhraní](../ide/implement-interface-wizard.md) (jenom z třídy ovládacího prvku)<br />- [Přidat bod připojení](../ide/implement-connection-point-wizard.md) (jenom třída ATL)<br />- [Přidat metodu](../ide/add-method-wizard.md) (jenom z rozhraní)<br />- [Přidat vlastnost](../ide/names-add-property-wizard.md) (pouze z rozhraní)<br />- [Přidat událost](../ide/add-event-wizard.md) (jenom z třídy ovládacího prvku)<br /><br />Výběrem Přidat třídu se otevře dialogové okno **Přidat třídu** , které vám umožní přístup ke všem novým průvodcům přidáním kódu třídy.|

## <a name="see-also"></a>Viz také

[Přepsání virtuální funkce](../ide/overriding-a-virtual-function-visual-cpp.md)<br>
[Procházení základu C++ kódu v aplikaci Visual Studio](../ide/navigate-code-cpp.md)<br>
[C++typy projektů v aplikaci Visual Studio](../build/reference/visual-cpp-project-types.md)<br>
[Typy souborů vytvořených pro projekty sady C++ Visual Studio](../build/reference/file-types-created-for-visual-cpp-projects.md)
