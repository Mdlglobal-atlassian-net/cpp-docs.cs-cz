---
title: Seznámení s kroky vlastního sestavení a s událostmi sestavení
ms.date: 08/29/2019
helpviewer_keywords:
- builds [C++], events
- custom build steps [C++], customizing builds
- events [C++], build
- custom build steps [C++]
- build steps [C++]
- build events [C++], order of events and build steps
- build steps [C++], build events
- builds [C++], custom build steps
ms.assetid: beb2f017-3e9f-4b2c-9b57-2572fd2628e4
ms.openlocfilehash: 386a12213814e3825ece8a81d61ac251c6793f43
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177322"
---
# <a name="understanding-custom-build-steps-and-build-events"></a>Seznámení s kroky vlastního sestavení a s událostmi sestavení

V rámci Visual C++ vývojového prostředí existují tři základní způsoby přizpůsobení procesu sestavení:

- **Vlastní kroky sestavení**

   Vlastní krok sestavení je pravidlo sestavení přidružené k projektu. Vlastní krok sestavení může určovat příkazový řádek, který se má provést, všechny další vstupní nebo výstupní soubory a zprávu, která se má zobrazit. Další informace najdete v tématu [Postup: Přidání vlastního kroku sestavení do projektů MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md).

- **Nástroje pro vlastní sestavení**

   Vlastní nástroj sestavení je pravidlo sestavení přidružené k jednomu nebo více souborům. Vlastní krok sestavení může předat vstupní soubory vlastnímu nástroji sestavení, což vede k jednomu nebo více výstupním souborům. Například soubory s nápovědu v aplikaci knihovny MFC jsou vytvořeny pomocí vlastního nástroje sestavení. Další informace naleznete v tématu [Postupy: Přidání vlastních nástrojů sestavení do projektů MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md) a [určení vlastních nástrojů sestavení](specifying-custom-build-tools.md).

- **Události sestavení**

   Události sestavení umožňují přizpůsobit sestavení projektu. Existují tři události sestavení: *před sestavením*, *před odkazem*a *po sestavení*. Událost sestavení umožňuje zadat akci, která se má provést v konkrétní době procesu sestavení. Můžete například použít událost sestavení k registraci souboru nástroje **regsvr32. exe** po dokončení sestavení projektu. Další informace naleznete v tématu [Určení událostí sestavení](specifying-build-events.md).

[Řešení potíží s přizpůsobením sestavení](troubleshooting-build-customizations.md) vám umožní zajistit, aby vlastní kroky sestavení a události sestavení běžely podle očekávání.

Výstupní formát vlastního kroku sestavení nebo události sestavení může také zlepšit použitelnost tohoto nástroje. Další informace naleznete v tématu [formátování výstupu vlastního kroku sestavení nebo události sestavení](formatting-the-output-of-a-custom-build-step-or-build-event.md).

Pro každý projekt v řešení jsou události sestavení a vlastní kroky sestavení spouštěny v následujícím pořadí spolu s dalšími kroky sestavení:

1. Událost před sestavením

2. Vlastní nástroje sestavení pro jednotlivé soubory

3. MIDL

4. Kompilátor prostředků

5. Kompilátor C/C++

6. událost před propojením

7. Linker nebo Librarian (podle potřeby)

8. Nástroj manifest

9. BSCMake

10. Vlastní krok sestavení v projektu

11. Událost po sestavení

A `custom build step on the project` `post-build event` spustí se postupně po dokončení všech ostatních procesů sestavení.

## <a name="in-this-section"></a>V tomto oddílu

[Určení nástrojů vlastního sestavení](specifying-custom-build-tools.md)<br/>
[Zadat události sestavení](specifying-build-events.md)<br/>
[Řešení potíží s přizpůsobením sestavení](troubleshooting-build-customizations.md)<br/>
[Formátovaní výstupu kroku vlastního sestavení nebo události sestavení](formatting-the-output-of-a-custom-build-step-or-build-event.md)

## <a name="see-also"></a>Viz také

[Projekty sady Visual Studio – C++](creating-and-managing-visual-cpp-projects.md)<br>
[Společná makra pro příkazy a vlastnosti sestavení](reference/common-macros-for-build-commands-and-properties.md)
