---
title: Seznámení s kroky vlastního sestavení a s událostmi sestavení
ms.date: 11/04/2016
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
ms.openlocfilehash: 5bc402ad8999f1864c7e6b1155da3c68862dda97
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823372"
---
# <a name="understanding-custom-build-steps-and-build-events"></a>Seznámení s kroky vlastního sestavení a s událostmi sestavení

Z vývojového prostředí Visual C++ existují tři základní způsoby, jak přizpůsobit proces sestavení:

- **Vlastní kroky sestavení**

   Vlastní krok sestavení je pravidlo sestavení přidružené k projektu. Vlastní krok sestavení můžete zadat příkazový řádek ke spuštění jakékoli další vstupní nebo výstupní soubory a napište zprávu zobrazit. Další informace najdete v tématu [jak: Přidat vlastní krok sestavení do projektů MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md).

- **Vlastní sestavovací nástroje**

   Pro vlastní nástroj sestavení je pravidlo sestavení přidružené k jedné nebo více souborů. Vlastní krok sestavení můžete předat vstupních souborů pro vlastní nástroj sestavení, což vede k jedné nebo více výstupních souborů. Například soubory nápovědy v aplikacích MFC jsou vybaveny pro vlastní nástroj sestavení. Další informace najdete v tématu [jak: Přidání vlastních nástrojů sestavení do projektů MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md) a [zadání vlastního nástroje sestavení](specifying-custom-build-tools.md).

- **Události sestavení**

   Události sestavení umožňují přizpůsobit sestavení projektu. Existují tři události sestavení: *před sestavením*, *před propojením*, a *po sestavení*. Události sestavení umožňuje určit akci na určitou dobu v procesu sestavení. Můžete například použít událost sestavení zaregistrovat soubor s **regsvr32.exe** po dokončení sestavení projektu. Další informace najdete v tématu [určení událostí sestavení](specifying-build-events.md).

[Řešení potíží s přizpůsobením sestavení](troubleshooting-build-customizations.md) vám může pomoct zajistit, aby vaše vlastní kroky sestavení a události sestavení fungovaly podle očekávání.

Formát výstupu vlastního kroku sestavení nebo události sestavení můžete také zlepšují použitelnost nástroje. Další informace najdete v tématu [Formátovaní výstupu vlastního kroku sestavení nebo události sestavení](formatting-the-output-of-a-custom-build-step-or-build-event.md).

Události sestavení a vlastní kroky v uvedeném pořadí společně s další kroky sestavení spustit sestavení:

1. Událost před sestavením

2. Nástroj Custom build na jednotlivé soubory

3. MIDL

4. Kompilátor prostředků

5. Kompilátor C/C++

6. událost před propojením

7. Propojovací program nebo Librarian (podle potřeby)

8. Nástroj manifest

9. BSCMake

10. Vlastní krok sestavení na projektu

11. Událost po sestavení

`custom build step on the project` a `post-build event` spustit postupně po všech ostatních vytvoření zpracovává dokončit.

## <a name="in-this-section"></a>V tomto oddílu

[Určení vlastních sestavovacích nástrojů](specifying-custom-build-tools.md)<br/>
[Určení událostí sestavení](specifying-build-events.md)<br/>
[Řešení potíží s přizpůsobením sestavení](troubleshooting-build-customizations.md)<br/>
[Formát výstupu vlastního kroku sestavení nebo události sestavení](formatting-the-output-of-a-custom-build-step-or-build-event.md)<br/>

## <a name="see-also"></a>Viz také

[Visual Studio Projects - C++](creating-and-managing-visual-cpp-projects.md)<br>
[Běžná makra pro příkazy a vlastnosti sestavení](reference/common-macros-for-build-commands-and-properties.md)