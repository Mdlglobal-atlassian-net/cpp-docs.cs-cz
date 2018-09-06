---
title: -EXPORT (Export funkce) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
dev_langs:
- C++
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16ec6be15635ebfc085615015b1221231645970d
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894791"
---
# <a name="export-exports-a-function"></a>/EXPORT (export funkce)

Exportuje funkce podle názvu nebo pořadí nebo dat, z vaší aplikace.

## <a name="syntax"></a>Syntaxe

> **/ EXPORT:**<em>Název_položky</em>[**,\@**<em>ordinální</em>[**, NONAME**]] [**, DATA**]

## <a name="remarks"></a>Poznámky

S parametrem/Export je přebytečný můžete exportovat funkce z vaší aplikace tak, aby ostatní programy mohou volat funkci. Můžete také exportovat data. Exporty jsou obvykle definovány v knihovně DLL.

*Název_položky* je název položky funkci nebo data, jako je pro volající program. `ordinal` Určuje index v tabulce exportů v rozsahu od 1 do 65 535; Pokud nezadáte `ordinal`, odkaz přiřadí jednu. **NONAME** – klíčové slovo exportuje funkci pouze ordinální číslo, aniž by *Název_položky*.

**DATA** – klíčové slovo určuje, zda exportované položky datové položky. Datová položka v programu klienta musí být deklarovány pomocí **extern __declspec(dllimport)**.

Existují tři metody pro export definice, uvedené v doporučené pořadí podle používání:

1. [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) ve zdrojovém kódu

2. [EXPORTY](../../build/reference/exports.md) – příkaz souboru .def

3. Specifikaci/Export je přebytečný v příkazu LINK

Všechny tři metody je možné ve stejném programu. Při propojení buildů program, který obsahuje exporty, také vytvoří knihovnu importu, pokud souboru .exp se používá v sestavení.

ODKAZ použití dekorovaných formy identifikátory. Když se vytvoří soubor .obj, upraví kompilátor identifikátor. Pokud *Název_položky* je zadán v linkeru v jeho nedekorovaných formuláře (jak se zobrazí ve zdrojovém kódu), odkaz se pokusí shodovat s názvem. Pokud ji nemůžete najít unikátní shoda, odkaz vydá chybovou zprávu. Použití [DUMPBIN](../../build/reference/dumpbin-reference.md) nástroj zobrazíte [dekorovaných názvů](../../build/reference/decorated-names.md) forma identifikátoru, když je potřeba zadat do propojovacího programu.

> [!NOTE]
> Nezadávejte upravené podobě identifikátory jazyka C, které jsou deklarovány `__cdecl` nebo `__stdcall`.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

2. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

3. Zadejte možnost do **další možnosti** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
[Možnosti linkeru](../../build/reference/linker-options.md)