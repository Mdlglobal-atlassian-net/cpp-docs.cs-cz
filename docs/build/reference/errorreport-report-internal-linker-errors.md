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
ms.openlocfilehash: 97d36e9db342e5873fc76a156b879e03af880dbf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447236"
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

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Otevřít **vlastnosti konfigurace** > **Linkeru** > **Upřesnit** stránku vlastností.

1. Upravit **zpráv o chybách** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Viz také:

[/errorReport (vytvoření sestavy s interními chybami kompilátoru)](../../build/reference/errorreport-report-internal-compiler-errors.md)<br/>
[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
