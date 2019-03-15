---
title: Sdílené složky nebo resuse nastavení sady Visual Studio project - C++
ms.date: 11/28/2018
helpviewer_keywords:
- project properties [C++], reusable
ms.openlocfilehash: 50e3795a4708a3c15ed25ee7ff6565470ef6989a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823412"
---
# <a name="share-or-resuse-visual-studio-project-settings"></a>Sdílené složky nebo resuse nastavení projektu Visual Studio

Chcete-li vytvořit vlastní skupiny nastavení, které můžete sdílet s ostatními uživateli nebo znovu použít ve více projektech, použijte **Správce vlastností** k vytvoření *vlastností* (soubor PROPS) k uložení nastavení pro každý druh projekt, který chcete moci opakovaně používat nebo sdílet s ostatními. Pomocí vlastnosti stylů je mnohem méně náchylný než jiné způsoby vytvoření "globální" nastavení. 

> [!IMPORTANT]
> **soubory .user a proč jsou problematické**
>
> Dřívější verze sady Visual Studio používaly globální tabulky vlastnosti, které měly příponu názvu souboru .user a byly umístěny ve \<userprofile > \AppData\Local\Microsoft\MSBuild\v4.0\ složky. Použití těchto souborů již nedoporučujeme, protože nastavují vlastnosti konfigurace projektu pro jednotlivé uživatele a počítače. Taková „globální“ nastavení mohou narušovat sestavení, zvláště když v sestavovacím počítači cílíte na více platforem. Pokud například máte projekt na platformě MFC i na platformě Windows Phone, vlastnosti v seznamu .user budou pro jeden z těchto projektů neplatné. Opakovaně použitelné seznamy vlastností jsou pružnější a odolnější.
>
> Přestože soubory .user se v sadě Visual Studio stále instalují a účastní se dědění vlastností, jsou ve výchozím nastavení prázdné. Osvědčeným postupem je odstranit odkazy na ně ve **Správce vlastností** zajistit, že projekty pracují nezávisle na jakémkoli uživatelské nastavení vázané na počítač to je důležité k zajištění správného chování v SCC (zdrojový kód ovládací prvek) prostředí.

Chcete-li zobrazit **Správce vlastností**, na panelu nabídek zvolte **zobrazení**, **ostatní Windows**, **Správce vlastností**.

Pokud máte běžnou, často používanou sadu vlastností, které chcete použít pro více projektů, můžete použít **Správce vlastností** k jejich zachycení do opakovaně použitelného *vlastností* soubor, který má přípona názvu souboru .props. Seznam (případně více seznamů) lze použít u nových projektů, takže nemusíte nastavovat jejich vlastnosti od začátku. Pro přístup k **Správce vlastností**, na panelu nabídek zvolte **zobrazení**, **Správce vlastností**.

![Správce vlastností nabídku](media/sharingnew.png "SharingNew")

Za každý uzel konfigurace najdete v článku uzly pro každý seznam vlastností, které platí pro tuto konfiguraci. Systém přidá seznam vlastností, které nastavte hodnoty podle možnosti zvolené v Průvodci vytvořením aplikace při vytváření projektu. Klikněte pravým tlačítkem na libovolný uzel a vyberte vlastnosti, které chcete zobrazit vlastnosti, které se vztahují k tomuto uzlu. Všechny seznamy vlastností jsou automaticky importovány do projektu "hlavní" vlastností (ms.cpp.props) a jsou vyhodnocovány v pořadí, ve kterém se zobrazují v Správce vlastností. Můžete je změnit pořadí vyhodnocování přesunout. Seznamy vlastností, které jsou vyhodnoceny později přepíšou hodnoty v tabulkách dříve vyhodnocen. Zobrazit [dědičnosti vlastností projektu](project-property-inheritance.md) Další informace o pořadí vyhodnocování v souboru .vcxproj, souborech .props a .targets, proměnné prostředí a příkazového řádku.

Pokud se rozhodnete **přidat nový seznam vlastností projektu** a vyberete například vlastností myprops.props, dialogové okno stránky vlastností zobrazí se. Všimněte si, že se týká seznamu vlastností MyProps. Jakékoli provedené změny se zapíší do tohoto seznamu, nikoli do souboru projektu (.vcxproj).

Pokud je stejná vlastnost nastavena přímo v souboru .vcxproj, vlastnosti v seznamu vlastností se přepíší.

Seznam vlastností můžete importovat tak často, jak potřebujete. Z jednoho seznamu vlastností může zdědit nastavení více projektů v řešení a projekt může obsahovat více seznamů. Samotný seznam vlastností může zdědit nastavení z jiného seznamu vlastností.

Můžete také vytvořit jeden seznam vlastností pro více konfigurací. K tomuto účelu vytvořte seznam vlastností pro každou konfiguraci, otevřete místní nabídku pro jeden z nich, zvolte **přidat existující seznam vlastností**a pak přidejte další listy. Pokud však používáte jeden společný seznam vlastností, nezapomeňte, že nastavená vlastnost se použije ve všech konfiguracích, ke kterým se seznam vztahuje, a že integrované vývojové prostředí neuvádí, které projekty nebo jiné seznamy vlastností z daného seznamu vlastností dědí.

V rozsáhlých řešeních, která budou obsahovat mnoho projektů, může být užitečné vytvořit seznam vlastností na úrovni řešení. Když přidáte projekt do řešení, použijte **Správce vlastností** do projektu přidat tento seznam vlastností. Pokud je to nutné na úrovni projektu, můžete přidat nový seznam vlastností, kterým se nastaví hodnoty specifické pro projekt.

> [!IMPORTANT]
> Soubor .props ve výchozím nastavení není součástí řízení zdroje, protože není vytvořen jako položka projektu. Pokud chcete soubor zahrnout do zdrojového kódu, můžete ho přidat ručně jako položku řešení.

#### <a name="to-create-a-property-sheet"></a>Vytvoření seznamu vlastností

1. V panelu nabídky zvolte **zobrazení**, **Správce vlastností**. **Správce vlastností** otevře.

2. Chcete-li definovat rozsah seznamu vlastností, vyberte položku, na kterou se vztahuje. Může se jednat o konkrétní konfiguraci nebo o jiný seznam vlastností. Otevřete místní nabídku pro tuto položku a klikněte na tlačítko **přidat nový seznam vlastností projektu**. Zadejte název a umístění seznamu.

3. V **Správce vlastností**, otevřete nový seznam vlastností a potom nastavte vlastnosti, které chcete zahrnout.
