---
title: Vlastnosti linkeru Clang (Android C++)
ms.date: 10/23/2017
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
f1_keywords:
- VC.Project.VCLinkerTool.Clang.OutputFile
- VC.Project.VCLinkerTool.Clang.Soname
- VC.Project.VCLinkerTool.Clang.ShowProgress
- VC.Project.VCLinkerTool.Clang.Version
- VC.Project.VCLinkerTool.Clang.VerboseOutput
- VC.Project.VCLinkerTool.Clang.IncrementalLink
- VC.Project.VCLinkerTool.Clang.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.Clang.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.Clang.UnresolvedReferences
- VC.Project.VCLinkerTool.Clang.OptimizeForMemory
- VC.Project.VCLinkerTool.Clang.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.Clang.ForceSymbolReferences
- VC.Project.VCLinkerTool.Clang.ForceFileOutput
- VC.Project.VCLinkerTool.Clang.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.Clang.GenerateMapFile
- VC.Project.VCLinkerTool.Clang.Relocation
- VC.Project.VCLinkerTool.Clang.FunctionBinding
- VC.Project.VCLinkerTool.Clang.NoExecStackRequired
- VC.Project.VCLinkerTool.Clang.WholeArchive
- VC.Project.VCLinkerTool.Clang.AdditionalOptionsPage
- VC.Project.VCLinkerTool.Clang.AdditionalDependencies
- VC.Project.VCLinkerTool.Clang.LibraryDependencies
ms.openlocfilehash: 55b944040157d13741b992f4ec66c35d1b117d95
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446534"
---
# <a name="clang-linker-properties-android-c"></a>Vlastnosti linkeru Clang ( C++Android)

| Vlastnost | Popis | Vlastnit |
|--|--|--|
| Výstupní soubor | Možnost přepíše výchozí název a umístění programu, který vytvoří linker. (-o) |
| Zobrazit průběh | Zobrazí zprávy o průběhu linkeru. |
| Verze | Možnost-Version dá linkeru pokyn, aby vložil číslo verze do hlavičky spustitelného souboru. |
| Povolit podrobný výstup | Možnost-verbose dá linkeru pokyn, aby výstupem podrobných zpráv pro ladění. |
| Povolit přírůstkové propojování | Možnost dá linkeru pokyn, aby umožnil přírůstkové propojování. |
| Cesta pro hledání sdílené knihovny | Umožňuje uživateli naplnit cestu pro hledání ve sdílené knihovně. |
| Další adresáře knihoven | Umožňuje uživateli přepsat cestu ke knihovně prostředí. (-L složka). |
| Oznamovat nevyřešené odkazy na symboly | Tato možnost, pokud je povolena sestava nevyřešené odkazy na symboly. |
| Optimalizovat využití paměti | Optimalizuje využití paměti přečtením tabulek symbolů podle potřeby. |
| Ignorovat specifické výchozí knihovny | Určuje jeden nebo více názvů výchozích knihoven, které se mají ignorovat. |
| Vynutit odkazy na symboly | Vynutí zadání symbolu do výstupního souboru jako nedefinovaného symbolu. |
| Informace o symbolech ladicího programu | Informace o symbolech ladicího programu z výstupního souboru. | **Zahrnout vše**<br /><br />**Vynechat nepotřebné symboly pro zpracování přemístění**<br /><br />**Vynechat jenom informace o symbolech ladicího programu**<br /><br />**Vynechat všechny informace o symbolech** |
| Informace o symbolu ladicího programu balíčku | Před zabalením přepruhujte informace o symbolech ladicího programu.  Pro ladění se používá kopie původního binárního souboru. |
| Název souboru mapy | Možnost map dá linkeru pokyn, aby vytvořil soubor mapy se zadaným uživatelským jménem. |
| Označit proměnné jen pro čtení po přemístění | Tato možnost označí proměnné po přemístění jen pro čtení. |
| Povolit okamžitou vazbu funkcí | Tato možnost označí objekt pro okamžité vázání funkcí. |
| Vyžadovat spustitelný zásobník | Tato možnost označuje výstup, který nevyžaduje spustitelný zásobník. |
| Celý archiv | Celý archiv používá veškerý kód ze zdrojů a dalších závislostí. |
| Další možnosti | Další možnosti |
| Další závislosti | Určuje další položky, které se mají přidat do příkazového řádku propojení. |
| Závislosti knihoven | Tato možnost umožňuje zadat další knihovny, které mají být přidány do příkazového řádku linkeru. Další knihovny jsou přidány na konec příkazového řádku linkeru Start s nástrojem *lib* a končí příponou *. a* nebo *. so* .  (-lFILE) |
