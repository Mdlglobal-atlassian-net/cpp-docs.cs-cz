---
title: -MANIFESTUAC (vložené informace UAC v manifestu) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
dev_langs:
- C++
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8c8c3cc219f0cf658dc2669ccc10adf3aba55bd
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163527"
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC (vložené informace UAC v manifestu)

Určuje, zda informace o řízení uživatelských účtů (UAC) je vloženy do manifestu.

## <a name="syntax"></a>Syntaxe

```
/MANIFESTUAC
/MANIFESTUAC:NO
/MANIFESTUAC:fragment
/MANIFESTUAC:level=_level
/MANIFESTUAC:uiAccess=_uiAccess
```

### <a name="parameters"></a>Parametry

*Fragment*<br/>
Řetězec, ve kterém `level` a `uiAccess` hodnoty. Další informace najdete v části poznámky dále v tomto tématu.

*ú_roveň*<br/>
Jeden z *asInvoker*, *highestAvailable*, nebo *requireAdministrator*. Výchozí hodnota je asInvoker. Další informace najdete v části poznámky dále v tomto tématu.

*_uiAccess*<br/>
**Hodnota TRUE** Pokud chcete aplikace obejít úrovně ochrany uživatelského rozhraní a jednotka vstup na vyšší oprávnění windows na ploše; v opačném případě **false**. Výchozí hodnota je **false**. Nastavte na **true** pouze pro uživatelské rozhraní aplikace.

## <a name="remarks"></a>Poznámky

Pokud zadáte více možností/MANIFESTUAC na příkazovém řádku, posledním blokem zadali přednost.

Možnosti pro /MANIFESTUAC:level jsou následující:

- `asInvoker`: Aplikace se spustí se stejnými oprávněními jako proces, který ji spustil. Aplikace může být zvýšena na vyšší úroveň oprávnění tak, že vyberete **spustit jako správce**.

- highestAvailable: aplikace se spustí s nejvyšší úrovní oprávnění, která se to dá. Pokud uživatel spustí aplikaci, která je členem skupiny Administrators, tato možnost je stejný jako requireAdministrator. Pokud je vyšší než úroveň při otevírání nejvyšší úroveň oprávnění k dispozici, systém zobrazí výzvu pro přihlašovací údaje.

- requireAdministrator: aplikace se spustí s oprávněními správce. Uživatel, který spustí aplikaci, která musí být členem skupiny Administrators. Pokud při otevírání neběží s oprávněními správce, systém zobrazí výzvu k zadání pověření.

Můžete zadat úroveň a uiAccess hodnoty v jednom kroku pomocí možnosti /MANIFESTUAC:fragment. Fragment musí být v následujícím tvaru:

```
"level=[ asInvoker | highestAvailable | requireAdministrator ] uiAccess=[ true | false ]"
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Rozbalte **Linkeru** uzlu.

1. Vyberte **soubor manifestu** stránku vlastností.

1. Upravit **povolit řízení uživatelských účtů (UAC)**, **úroveň spuštění nástroje Řízení uživatelských účtů**, a **ochrana UI nástroje Řízení uživatelských účtů** vlastnosti.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A>, a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)