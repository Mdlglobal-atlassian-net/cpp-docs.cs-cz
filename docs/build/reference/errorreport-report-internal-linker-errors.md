---
title: "-ERRORREPORT (sestava interními chybami Linkeru) | Microsoft Docs"
ms.custom: 
ms.date: 12/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
dev_langs: C++
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6ddf65ed2a17dae2d86b0dc4582f1d3158328898
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (sestava s interními chybami linkeru)

> **/ errorreport:**[ **žádné** | **řádku** | **fronty** | **odeslat** ]

## <a name="arguments"></a>Arguments

**None**  
Zprávy o chybách interní kompilátoru nebudou shromažďovány nebo odesílány do společnosti Microsoft.

**řádku**  
Dotaz, zda chcete poslat zprávu, když obdrží vnitřní chyby kompilátoru. **řádku** je výchozí hodnota při kompilaci aplikace ve vývojovém prostředí.

**fronty**  
Fronty zprávy o chybách. Když se přihlásíte pomocí oprávnění správce, tak, aby ohlásíte případných selhání od posledního byly přihlášení, zobrazí se okno (nezobrazí se výzva k odeslání zpráv o selhání více než jednou za tři dní). **fronty** je výchozí hodnota při kompilaci aplikace na příkazovém řádku.

**Odeslat**  
Pokud je povoleno oznamování nastavením služby zasílání zpráv o chybách systému Windows automaticky odesílá zprávy o chybách interní kompilátoru společnosti Microsoft.

## <a name="remarks"></a>Poznámky

**/Errorreport** možnost umožňuje zadat informace o chybě (LED) interní kompilátoru přímo společnosti Microsoft.

Možnost **/errorreport:send** automaticky odesílá informace o chybách společnosti Microsoft, pokud je povoleno nastavením služby zasílání zpráv o chybách systému Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Otevřete **vlastnosti konfigurace** > **Linkeru** > **Upřesnit** stránku vlastností.

1. Změnit **zasílání zpráv o chybách** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Viz také

[/ errorreport (sestava interními chybami kompilátoru)](../../build/reference/errorreport-report-internal-compiler-errors.md)  
[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)  
[Možnosti linkeru](../../build/reference/linker-options.md)  
