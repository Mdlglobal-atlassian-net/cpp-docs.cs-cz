---
title: Vytvoření projektu (ATL – tutoriál, část 1)
ms.custom: get-started-article
ms.date: 05/06/2019
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
ms.openlocfilehash: 292faf1769baa2e1c3fc6e52ba6df065cf08766e
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221402"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>Vytvoření projektu (ATL – tutoriál, část 1)

Tento kurz vás provede bez atributové projekt knihovny ATL, který vytvoří objekt ActiveX, který zobrazí mnohoúhelníku. Objekt obsahuje možnosti pro povolení uživatele Chcete-li změnit počet stran tvořící mnohoúhelníků a kódu, aktualizujte zobrazení.

> [!NOTE]
> ATL a MFC nejsou podporovány obecně v edicích Express sady Visual Studio.

> [!NOTE]
> Tento kurz vytvoří stejný zdrojový kód jako ukázka mnohoúhelníku. Pokud chcete se vyhnout ručním zadáním zdrojového kódu, můžete ji stáhnout [abstraktní ukázky mnohoúhelníku](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/Polygon). Poté můžete odkázat ke zdrojovému kódu mnohoúhelníku při projít tento kurz, a použít ho ke kontrole chyb ve vašem vlastním projektu.
> Chcete-li zkompilovat, otevřete stdafx.h a nahradit:
> ```
> #ifndef WINVER
> #define WINVER 0x0400
> #endif
> ```
> with
> ```
> #ifndef WINVER
> #define WINVER 0x0500
> #define _WIN32_WINNT 0x0500
> #endif
> ```
> Kompilátor bude stále stěžovat `regsvr32` není ukončováno, správně, ale které by měl mít pořád ovládacího prvku knihovny DLL sestavené a k dispozici pro použití.

### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>Chcete-li vytvořit počáteční projekt knihovny ATL pomocí Průvodce projektem ATL

1. V sadě Visual Studio 2017 a dříve: **Soubor** > **nové** > **projektu**. Otevřít **Visual C++**  kartě a vyberte **MFC nebo ATL**. Vyberte **projekt knihovny ATL**.

   In Visual Studio 2019: Zvolte **souboru** > **nový** > **projektu**, zadejte do vyhledávacího pole "atl" a zvolte **projekt knihovny ATL**.

1. Typ *mnohoúhelníku* jako název projektu.

    Umístění pro zdrojový kód se obvykle ve výchozím nastavení \Users\\\<uživatelské jméno > \source\repos a nové složky se vytvoří automaticky.

1. Klikněte na tlačítko **OK** a **projekt knihovny ATL** otevře se průvodce.

1. Klikněte na tlačítko **nastavení aplikace** chcete zobrazit dostupné možnosti.

1. Jako jsou vytvoření ovládacího prvku a ovládací prvek musí být v procesový server, ponechte **typ aplikace** jako knihovnu DLL.

1. U ostatních možností ponechte jejich výchozí hodnoty a klikněte na tlačítko **OK**.

**Průvodce projektem ATL** vytvoří vygenerováním několik souborů projektu. Můžete zobrazit tyto soubory v **Průzkumníka řešení** tak, že rozbalíte `Polygon` objektu. Soubory jsou uvedeny níže.

|Soubor|Popis|
|----------|-----------------|
|Polygon.cpp|Obsahuje implementaci `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`, a `DllUnregisterServer`. Obsahuje také mapy objektu, která je seznamu objektů knihovny ATL v projektu. Toto je původně prázdné.|
|Polygon.def|Tento soubor definice modulu poskytuje linkeru s informacemi o exportech vyžadované vaší knihovny DLL.|
|Polygon.IDL|Rozhraní language souboru definice, které popisuje specifické pro objekty rozhraní.|
|Polygon.rgs|Tento skript registru obsahuje informace o registraci knihovny DLL váš program.|
|Polygon.rc|Soubor prostředků, která původně obsahuje informace o verzi a řetězec obsahující název projektu.|
|Resource.h|Hlavičkový soubor pro soubor prostředků.|
|Polygonps.def|Tento soubor definice modulu poskytuje linkeru s informacemi o vývozu vyžadované kódu proxy a zástupných procedur, které podporují volání napříč objekty apartment.|
|stdafx.cpp|Soubor, který bude `#include` ATL implementační soubory.|
|stdafx.h|Soubor, který bude `#include` hlavičkové soubory ATL.|

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši `Polygon` projektu.

1. V místní nabídce klikněte na tlačítko **vlastnosti**.

1. Klikněte na **Linkeru**. Změnit **za UserRedirection** umožňuje **Ano**.

1. Klikněte na **OK**.

V dalším kroku přidáte ovládací prvek do projektu.

[Ke kroku 2](../atl/adding-a-control-atl-tutorial-part-2.md)

## <a name="see-also"></a>Viz také:

[Kurz](../atl/active-template-library-atl-tutorial.md)
