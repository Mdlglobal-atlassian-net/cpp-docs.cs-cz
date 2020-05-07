---
title: Řešení potíží s přizpůsobením sestavení
ms.date: 11/04/2016
helpviewer_keywords:
- build events [C++], troubleshooting
- builds [C++], build events
- troubleshooting [C++], builds
- build steps [C++], troubleshooting
- events [C++], build
- builds [C++], troubleshooting
- custom build steps [C++], troubleshooting
ms.assetid: e4ceb177-fbee-4ed3-a7d7-80f0d78c1d07
ms.openlocfilehash: 7a45b449dc9c3c4c81add37bbac0813c81133203
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315245"
---
# <a name="troubleshooting-build-customizations"></a>Řešení potíží s přizpůsobením sestavení

Pokud se vlastní kroky sestavení nebo události nechovají podle očekávání, existuje několik věcí, které se snažíte pochopit, co je chybné.

- Ujistěte se, že soubory, které vlastní kroky sestavení generují, odpovídají souborům, které deklarujete jako výstupy.

- Pokud vlastní kroky sestavení generují všechny soubory, které jsou vstupy nebo závislosti dalších kroků sestavení (vlastní nebo jinak), ujistěte se, že jsou tyto soubory přidány do projektu. A ujistěte se, že jsou nástroje, které tyto soubory používají, spouštěny po vlastním kroku sestavení.

- Chcete-li zobrazit, co vlastní krok sestavení skutečně dělá, `@echo on` přidejte jako první příkaz. Události sestavení a kroky sestavení jsou vloženy do dočasného souboru. bat a spustí se, když je projekt sestaven. Proto můžete přidat kontrolu chyb na událost sestavení nebo příkazy kroku sestavení.

- Zkontrolujte protokol sestavení v adresáři zprostředkující soubory, abyste viděli, co skutečně bylo provedeno. Cesta a název protokolu sestavení jsou reprezentovány výrazem makra **MSBuild** , **$ (IntDir)\\$ (MSBuildProjectName). log**.

- Upravte nastavení projektu tak, aby shromáždilo více než výchozí množství informací v protokolu sestavení. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti). V dialogovém okně **Možnosti** klikněte na uzel **projekty a řešení** a potom klikněte na uzel **sestavení a spuštění** . Pak v poli **podrobností souboru protokolu sestavení projektu MSBuild** klikněte na **podrobné**.

- Ověřte hodnoty libovolného názvu souboru nebo makra adresáře, které používáte. Makra můžete zobrazovat jednotlivě nebo můžete přidat `copy %0 command.bat` na začátek vlastního kroku sestavení, který zkopíruje příkazy vlastního kroku sestavení do příkazu Command. bat se všemi rozbalenými makry.

- Spouštějte vlastní kroky sestavení a události sestavení jednotlivě a ověřte jejich chování.

## <a name="see-also"></a>Viz také

[Seznámení s kroky vlastního sestavení a s událostmi sestavení](understanding-custom-build-steps-and-build-events.md)
