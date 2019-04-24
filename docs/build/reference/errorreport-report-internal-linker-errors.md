---
title: /ERRORREPORT (sestava s interními chybami linkeru)
ms.date: 12/28/2017
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
ms.openlocfilehash: 26cc157cb7247a3a2ea7c10b415df1160540c9ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271726"
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (sestava s interními chybami linkeru)

> **/ errorreport:**[ **žádný** | **řádku** | **fronty** | **odeslat** ]

## <a name="arguments"></a>Arguments

**None**<br/>
Sestavy o vnitřních chybách kompilátoru nebudou shromážděné nebo odeslané společnosti Microsoft.

**prompt**<br/>
Zobrazí výzvu k odeslání hlášení, pokud obdržíte chybu kompilátoru. **řádek** výchozí nastavení je při kompilaci aplikace ve vývojovém prostředí.

**fronty**<br/>
Zařadí do fronty zprávy o chybách. Při přihlašování s použitím oprávnění správce, takže můžete nahlásit všechny chyby od posledního byly zaznamenány v, zobrazí se okno (nezobrazí se výzva k odeslání zprávy o chybách více než jednou za tři dny). **fronty** výchozí nastavení je při kompilaci aplikace příkazového řádku.

**Odeslat**<br/>
Automaticky odesílá zprávy o vnitřních chybách kompilátoru společnosti Microsoft, pokud je povoleno oznamování nastavením služby zasílání zpráv o chybách Windows.

## <a name="remarks"></a>Poznámky

**/Errorreport** možnost vám umožňuje poskytnout informace o kompilátoru vnitřní chybě (ICE) přímo společnosti Microsoft.

Možnost **/errorreport: send** automaticky odesílá informace o chybách společnosti Microsoft, pokud je povoleno zasílání zpráv o chybách Windows nastavení služby.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Otevřít **vlastnosti konfigurace** > **Linkeru** > **Upřesnit** stránku vlastností.

1. Upravit **zpráv o chybách** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Viz také:

[/errorReport (vytvoření sestavy s interními chybami kompilátoru)](errorreport-report-internal-compiler-errors.md)<br/>
[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
