---
title: Vytvoření projektu (ATL – tutoriál, část 1)
ms.custom: get-started-article
ms.date: 08/19/2019
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
ms.openlocfilehash: 31ecee084f620256820a685df1f0e6891046fb8f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075335"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>Vytvoření projektu (ATL – tutoriál, část 1)

Tento kurz vás provede jednotlivými kroky prostřednictvím neatributového projektu ATL, který vytvoří objekt ActiveX, který zobrazí mnohoúhelník. Objekt obsahuje možnosti umožňující uživateli změnit počet stran, které tvoří mnohoúhelník, a kód pro aktualizaci zobrazení.

> [!NOTE]
> V tomto kurzu se vytvoří stejný zdrojový kód jako ukázka mnohoúhelníku. Pokud se chcete vyhnout ručnímu zadávání zdrojového kódu, můžete si ho stáhnout z [ukázkového abstraktního mnohoúhelníku](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/Polygon). Pak se můžete podívat na zdrojový kód mnohoúhelníku při práci v kurzu nebo ho použít ke kontrole chyb ve vašem projektu.
> Chcete-li kompilovat, otevřete soubor *PCH. h* (*stdafx. h* v aplikaci Visual Studio 2017 a starší) a nahraďte:
>
> ```
> #ifndef WINVER
> #define WINVER 0x0400
> #endif
> ```
>
> následující adresou:
>
> ```
> #ifndef WINVER
> #define WINVER 0x0500
> #define _WIN32_WINNT 0x0500
> #endif
> ```
>
> Kompilátor bude stále vystavovat `regsvr32` neukončí správně, ale měli byste mít stále vytvořenou knihovnu DLL ovládacího prvku a je k dispozici pro použití.

### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>Vytvoření počátečního projektu ATL pomocí Průvodce projektem ATL

1. V aplikaci Visual Studio 2017 a starší: **soubor** > **Nový** > **projekt**. Otevřete kartu **vizuál C++**  a vyberte **MFC/ATL**. Vyberte **projekt ATL**.

   V aplikaci Visual Studio 2019: vyberte **soubor** > **Nový** > **projekt**, do vyhledávacího pole zadejte "ATL" a klikněte na **projekt ATL**.

1. Jako název projektu zadejte *mnohoúhelník* .

    Umístění zdrojového kódu bude obvykle ve výchozím nastavení na \Users\\\<username > \source\repos a automaticky se vytvoří nová složka.

1. V aplikaci Visual Studio 2019 přijměte výchozí hodnoty a klikněte na tlačítko **OK**.
   V aplikaci Visual Studio 2017 kliknutím na tlačítko **OK** otevřete průvodce **projektem ATL** . Kliknutím na **nastavení aplikace** zobrazíte dostupné možnosti. Vzhledem k tomu, že tento projekt vytvoří ovládací prvek a ovládací prvek musí být v procesovém serveru, ponechte **Typ aplikace** jako knihovnu DLL. Klikněte na tlačítko **OK**.

Visual Studio vytvoří projekt generováním několika souborů. Tyto soubory můžete zobrazit v **Průzkumník řešení** rozbalením objektu `Polygon`. Níže jsou uvedené soubory.

::: moniker range="<=vs-2017"

|File|Popis|
|----------|-----------------|
|Polygon.cpp|Obsahuje implementaci `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`a `DllUnregisterServer`. Obsahuje také mapu objektu, což je seznam objektů ATL v projektu. Toto je zpočátku prázdné.|
|Mnohoúhelník. def|Tento soubor definice modulu poskytuje linkeru informace o exportech vyžadovaných vaší knihovnou DLL.|
|Mnohoúhelník. idl|Soubor jazyka definice rozhraní, který popisuje rozhraní specifická pro vaše objekty.|
|Mnohoúhelník. rgs|Tento skript registru obsahuje informace pro registraci knihovny DLL programu.|
|Polygon.rc|Soubor prostředků, který zpočátku obsahuje informace o verzi a řetězec obsahující název projektu.|
|Resource.h|Hlavičkový soubor pro soubor prostředků|
|Polygonps. def|Tento soubor definice modulu poskytuje linkeru informace o exportech vyžadovaných proxy a zástupným kódem, který podporuje volání přes objekty Apartment.|
|stdafx.cpp|Soubor, který bude `#include` *stdafx. h*.|
|stdafx.h|Soubor, který bude `#include` a předkompilovat hlavičkové soubory ATL.|

::: moniker-end

::: moniker range=">=vs-2019"

|File|Popis|
|----------|-----------------|
|Polygon.cpp|Obsahuje implementaci `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`a `DllUnregisterServer`. Obsahuje také mapu objektu, což je seznam objektů ATL v projektu. Toto je zpočátku prázdné.|
|Mnohoúhelník. def|Tento soubor definice modulu poskytuje linkeru informace o exportech vyžadovaných vaší knihovnou DLL.|
|Mnohoúhelník. idl|Soubor jazyka definice rozhraní, který popisuje rozhraní specifická pro vaše objekty.|
|Mnohoúhelník. rgs|Tento skript registru obsahuje informace pro registraci knihovny DLL programu.|
|Polygon.rc|Soubor prostředků, který zpočátku obsahuje informace o verzi a řetězec obsahující název projektu.|
|Resource.h|Hlavičkový soubor pro soubor prostředků|
|Polygonps. def|Tento soubor definice modulu poskytuje linkeru informace o exportech vyžadovaných proxy a zástupným kódem, který podporuje volání přes objekty Apartment.|
|PCH. cpp|Soubor, který bude `#include` *PCH. h*.|
|PCH. h|Soubor, který bude `#include` a předkompilovat hlavičkové soubory ATL.|

::: moniker-end

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt `Polygon`.

1. V místní nabídce klikněte na **vlastnosti**.

1. Klikněte na **linker**. Změňte možnost **podle UserRedirection** na **Ano**.

1. Klikněte na tlačítko **OK**.

V dalším kroku přidáte ovládací prvek do projektu.

[Ke kroku 2](../atl/adding-a-control-atl-tutorial-part-2.md)

## <a name="see-also"></a>Viz také

[Kurz](../atl/active-template-library-atl-tutorial.md)
