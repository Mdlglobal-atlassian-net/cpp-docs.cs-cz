---
title: Sdílení nebo opakované použití nastavení projektu sady Visual Studio –C++
ms.date: 07/17/2019
helpviewer_keywords:
- project properties [C++], reusable
ms.openlocfilehash: 9a8f6da3dc754aa9d47d46e26207a02bd1685ea8
ms.sourcegitcommit: 610751254a01cba6ad15fb1e1764ecb2e71f66bf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/18/2019
ms.locfileid: "68313192"
---
# <a name="share-or-reuse-visual-studio-project-settings"></a>Sdílení a opakované použití nastavení projektu sady Visual Studio

Chcete-li vytvořit vlastní skupinu nastavení, která můžete sdílet s ostatními nebo je použít ve více projektech, použijte **Správce vlastností** k vytvoření *seznamu vlastností* (soubor. props) pro uložení nastavení pro každý typ projektu, který chcete mít možnost znovu použít nebo sdílet. s ostatními. Používání seznamů vlastností je mnohem méně náchylné k chybám než jiné způsoby vytváření "globálních" nastavení. 

> [!IMPORTANT]
> **soubory. User a proč jsou problematické**
>
> Starší verze sady Visual Studio používaly globální seznamy vlastností, které mají příponu názvu souboru. User a byly umístěny ve \<složce USERPROFILE > \AppData\Local\Microsoft\MSBuild\v4.0\. Použití těchto souborů již nedoporučujeme, protože nastavují vlastnosti konfigurace projektu pro jednotlivé uživatele a počítače. Taková „globální“ nastavení mohou narušovat sestavení, zvláště když v sestavovacím počítači cílíte na více platforem. Pokud například máte projekt na platformě MFC i na platformě Windows Phone, vlastnosti v seznamu .user budou pro jeden z těchto projektů neplatné. Opakovaně použitelné seznamy vlastností jsou pružnější a odolnější.
>
> Přestože soubory .user se v sadě Visual Studio stále instalují a účastní se dědění vlastností, jsou ve výchozím nastavení prázdné. Osvědčeným postupem je odstranit odkaz na ně v **Správce vlastností** , aby se zajistilo, že vaše projekty budou fungovat nezávisle na jednotlivých uživatelích, nastavení jednotlivých počítačů je důležité k zajištění správného chování v prostředí SCC (řízení zdrojového kódu).

Chcete-li zobrazit **Správce vlastností**, na panelu nabídek vyberte možnost **Zobrazit** > **Správce vlastností** nebo **Zobrazit** > jiné**Správce vlastností** **systému Windows** > v závislosti na nastavení.

Pokud máte běžnou, často používanou sadu vlastností, které chcete použít pro více projektů, můžete použít **Správce vlastností** k jejich zachycení do opakovaně použitelného souboru *seznamu vlastností* , který má v konvenci příponu názvu souboru. props. Seznam (případně více seznamů) lze použít u nových projektů, takže nemusíte nastavovat jejich vlastnosti od začátku.

![Místní nabídka Správce vlastností](media/sharingnew.png "SharingNew")

V každém uzlu Konfigurace vidíte uzly pro každý seznam vlastností, který platí pro tuto konfiguraci. Systém přidá seznamy vlastností, které nastaví hodnoty na základě možností, které zvolíte v Průvodci aplikací při vytváření projektu. Klikněte pravým tlačítkem na libovolný uzel a vyberte vlastnosti. zobrazí se vlastnosti, které se vztahují na daný uzel. Všechny seznamy vlastností jsou automaticky importovány do "hlavního" seznamu vlastností projektu (MS. cpp. props) a jsou vyhodnocovány v pořadí, ve kterém jsou Správce vlastností. Můžete je přesunout, chcete-li změnit pořadí vyhodnocování. Seznamy vlastností, které jsou vyhodnocovány později, přepíšou hodnoty v dříve vyhodnocených listech. Viz [dědičnost vlastností projektu](project-property-inheritance.md) pro další informace o pořadí vyhodnocování v souboru. vcxproj, souborech. props a. targets, proměnných prostředí a příkazovém řádku.

Pokud zvolíte možnost **Přidat nový seznam vlastností projektu** a pak vyberete například seznam vlastností MyProps. props, zobrazí se dialogové okno Stránka vlastností. Všimněte si, že se týká seznamu vlastností MyProps. Jakékoli provedené změny se zapíší do tohoto seznamu, nikoli do souboru projektu (.vcxproj).

Pokud je stejná vlastnost nastavena přímo v souboru .vcxproj, vlastnosti v seznamu vlastností se přepíší.

Seznam vlastností můžete importovat tak často, jak potřebujete. Z jednoho seznamu vlastností může zdědit nastavení více projektů v řešení a projekt může obsahovat více seznamů. Samotný seznam vlastností může zdědit nastavení z jiného seznamu vlastností.

Můžete také vytvořit jeden seznam vlastností pro více konfigurací. Chcete-li to provést, vytvořte seznam vlastností pro každou konfiguraci, otevřete místní nabídku pro jednu z nich, zvolte možnost **Přidat existující seznam vlastností**a poté přidejte další listy. Pokud však používáte jeden společný seznam vlastností, nezapomeňte, že nastavená vlastnost se použije ve všech konfiguracích, ke kterým se seznam vztahuje, a že integrované vývojové prostředí neuvádí, které projekty nebo jiné seznamy vlastností z daného seznamu vlastností dědí.

V rozsáhlých řešeních, která budou obsahovat mnoho projektů, může být užitečné vytvořit seznam vlastností na úrovni řešení. Při přidání projektu do řešení použijte **Správce vlastností** k přidání tohoto seznamu vlastností do projektu. Pokud je to nutné na úrovni projektu, můžete přidat nový seznam vlastností, kterým se nastaví hodnoty specifické pro projekt.

> [!IMPORTANT]
> Soubor .props ve výchozím nastavení není součástí řízení zdroje, protože není vytvořen jako položka projektu. Pokud chcete soubor zahrnout do zdrojového kódu, můžete ho přidat ručně jako položku řešení.

#### <a name="to-create-a-property-sheet"></a>Vytvoření seznamu vlastností

1. Na panelu nabídek vyberte možnost **Zobrazit** > **Správce vlastností** nebo **Zobrazit** > další**Správce vlastností** **systému Windows** > . Otevře se **Správce vlastností** .

2. Chcete-li definovat rozsah seznamu vlastností, vyberte položku, na kterou se vztahuje. Může se jednat o konkrétní konfiguraci nebo o jiný seznam vlastností. Otevřete místní nabídku pro tuto položku a pak zvolte možnost **Přidat nový seznam vlastností projektu**. Zadejte název a umístění seznamu.

3. V **Správce vlastností**otevřete nový seznam vlastností a nastavte vlastnosti, které chcete zahrnout.
