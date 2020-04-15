---
title: Sdílení nebo opakované použití nastavení projektu sady Visual Studio – C++
ms.date: 07/17/2019
helpviewer_keywords:
- project properties [C++], reusable
ms.openlocfilehash: bcf54be0531c7150c1506eb6f5dda2b5bc95161f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328692"
---
# <a name="share-or-reuse-visual-studio-project-settings"></a>Sdílení a opakované použití nastavení projektu sady Visual Studio

Chcete-li vytvořit vlastní skupinu nastavení, která můžete sdílet s ostatními nebo je opakovaně použít ve více projektech, vytvořte pomocí **Správce vlastností** *(soubor.props)* nastavení pro každý druh projektu, který chcete znovu použít nebo sdílet s ostatními. Použití seznamů vlastností je mnohem méně náchylné k chybám než jiné způsoby vytváření "globálních" nastavení.

> [!IMPORTANT]
> **.user soubory a proč jsou problematické**
>
> Minulé verze sady Visual Studio používaly globální seznamy vlastností, které \<měly příponu .user file name extension a byly umístěny ve složce userprofile>\AppData\Local\Microsoft\MSBuild\v4.0\. Použití těchto souborů již nedoporučujeme, protože nastavují vlastnosti konfigurace projektu pro jednotlivé uživatele a počítače. Taková „globální“ nastavení mohou narušovat sestavení, zvláště když v sestavovacím počítači cílíte na více platforem. Pokud například máte projekt na platformě MFC i na platformě Windows Phone, vlastnosti v seznamu .user budou pro jeden z těchto projektů neplatné. Opakovaně použitelné seznamy vlastností jsou pružnější a odolnější.
>
> Přestože soubory .user se v sadě Visual Studio stále instalují a účastní se dědění vlastností, jsou ve výchozím nastavení prázdné. Osvědčeným postupem je odstranit odkaz na ně ve **Správci vlastností,** aby bylo zajištěno, že vaše projekty fungují nezávisle na všech nastaveních pro jednotlivé uživatele, počítače To je důležité pro zajištění správného chování v prostředí SCC (správa zdrojového kódu).

Chcete-li zobrazit **Správce vlastností**, zvolte v závislosti na nastavení na panelu nabídek možnost **Zobrazit** > **Správce vlastností** nebo **Zobrazit** > jiný**správce vlastností systému****Windows** > .

Pokud máte společnou, často používanou sadu vlastností, které chcete použít pro více projektů, můžete použít **Správce vlastností** k jejich zachycení v opakovaně použitelném souboru *seznamu vlastností,* který podle konvence má příponu .props název souboru. Seznam (případně více seznamů) lze použít u nových projektů, takže nemusíte nastavovat jejich vlastnosti od začátku.

![Místní nabídka Správce vlastností](media/sharingnew.png "SdíleníNovinka")

Pod každým konfiguračním uzlem se zobrazí uzly pro každý seznam vlastností, který se vztahuje k této konfiguraci. Systém přidá seznamy vlastností, které nastavují hodnoty na základě možností, které zvolíte v průvodci aplikací při vytváření projektu. Klikněte pravým tlačítkem myši na libovolný uzel a zvolte Vlastnosti, chcete-li zobrazit vlastnosti, které se vztahují k tomuto uzlu. Všechny seznamy vlastností jsou importovány automaticky do seznamu vlastností "hlavního" projektu (ms.cpp.props) a jsou vyhodnocovány v pořadí, v jakém jsou zobrazeny ve Správci vlastností. Můžete je přesunout a změnit pořadí hodnocení. Seznamy vlastností, které jsou vyhodnoceny později, přepíší hodnoty v dříve vyhodnocované listy. Další informace o pořadí vyhodnocení v souboru .vcxproj, souborech .props a .targets, proměnných prostředí a příkazovém řádku naleznete v tématu [Dědičnost vlastností aplikace Project.](project-property-inheritance.md)

Pokud zvolíte **Přidat nový seznam vlastností projektu** a pak vyberete například seznam vlastností MyProps.props, zobrazí se dialogové okno stránky vlastností. Všimněte si, že se týká seznamu vlastností MyProps. Jakékoli provedené změny se zapíší do tohoto seznamu, nikoli do souboru projektu (.vcxproj).

Pokud je stejná vlastnost nastavena přímo v souboru .vcxproj, vlastnosti v seznamu vlastností se přepíší.

Seznam vlastností můžete importovat tak často, jak potřebujete. Z jednoho seznamu vlastností může zdědit nastavení více projektů v řešení a projekt může obsahovat více seznamů. Samotný seznam vlastností může zdědit nastavení z jiného seznamu vlastností.

Můžete také vytvořit jeden seznam vlastností pro více konfigurací. Chcete-li to provést, vytvořte seznam vlastností pro každou konfiguraci, otevřete místní nabídku pro jednu z nich, zvolte **Přidat existující seznam vlastností**a pak přidejte další listy. Pokud však používáte jeden společný seznam vlastností, uvědomte si, že při nastavování vlastnosti se nastaví pro všechny konfigurace, na které se list vztahuje, a že ide nezobrazuje, které projekty nebo jiné seznamy vlastností dědí z daného seznamu vlastností.

V rozsáhlých řešeních, která budou obsahovat mnoho projektů, může být užitečné vytvořit seznam vlastností na úrovni řešení. Když přidáte projekt do řešení, přidejte tento seznam vlastností do projektu pomocí **Správce vlastností.** Pokud je to nutné na úrovni projektu, můžete přidat nový seznam vlastností, kterým se nastaví hodnoty specifické pro projekt.

> [!IMPORTANT]
> Soubor .props ve výchozím nastavení se neúčastní správy zdrojového kódu, protože není vytvořen jako položka projektu. Pokud chcete soubor zahrnout do zdrojového kódu, můžete ho přidat ručně jako položku řešení.

#### <a name="to-create-a-property-sheet"></a>Vytvoření seznamu vlastností

1. Na řádku nabídek zvolte **Zobrazit** > **Správce vlastností** nebo **Zobrazit** > jiný**Správce vlastností systému****Windows** > . Otevře se **Správce vlastností.**

2. Chcete-li definovat rozsah seznamu vlastností, vyberte položku, na kterou se vztahuje. Může se jednat o konkrétní konfiguraci nebo o jiný seznam vlastností. Otevřete místní nabídku pro tuto položku a pak zvolte **Přidat nový seznam vlastností projektu**. Zadejte název a umístění seznamu.

3. Ve **Správci vlastností**otevřete nový seznam vlastností a nastavte vlastnosti, které chcete zahrnout.
