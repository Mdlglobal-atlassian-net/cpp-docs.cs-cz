---
title: /EXPORT (export funkce)
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
ms.openlocfilehash: 7c4f4621bbccd4285bcf4eca07d2544d53d14f6c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819847"
---
# <a name="export-exports-a-function"></a>/EXPORT (export funkce)

Exportuje funkce podle názvu nebo pořadí nebo dat, z vaší aplikace.

## <a name="syntax"></a>Syntaxe

> **/ EXPORT:**<em>Název_položky</em>[**,\@**<em>ordinální</em>[**, NONAME**]] [**, DATA**]

## <a name="remarks"></a>Poznámky

**/EXPORT** určuje funkce nebo data položky pro export z vaší aplikace tak, aby ostatní programy můžete volat funkci nebo data. Exporty jsou obvykle definovány v knihovně DLL.

*Název_položky* je název položky funkci nebo data, jako je pro volající program. *ordinální* Určuje index v tabulce exportů v rozsahu od 1 do 65 535; Pokud nezadáte *ordinální*, odkaz přiřadí jednu. **NONAME** – klíčové slovo exportuje funkci pouze ordinální číslo, aniž by *Název_položky*.

**DATA** – klíčové slovo určuje, zda exportované položky datové položky. Datová položka v programu klienta musí být deklarovány pomocí **extern __declspec(dllimport)**.

Existují čtyři způsoby pro export definice, uvedené v doporučené pořadí podle používání:

1. [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) ve zdrojovém kódu

1. [EXPORTY](exports.md) – příkaz souboru .def

1. Specifikaci/Export je přebytečný v příkazu LINK

1. A [komentář](../../preprocessor/comment-c-cpp.md) směrnice ve zdrojovém kódu formuláře `#pragma comment(linker, "/export: definition ")`.

Všechny tyto metody můžete použít ve stejném programu. Při propojení buildů program, který obsahuje exporty, také vytvoří knihovnu importu, pokud souboru .exp se používá v sestavení.

ODKAZ použití dekorovaných formy identifikátory. Když se vytvoří soubor .obj, upraví kompilátor identifikátor. Pokud *Název_položky* je zadán v linkeru v jeho nedekorovaných formuláře (jak se zobrazí ve zdrojovém kódu), odkaz se pokusí shodovat s názvem. Pokud ji nemůžete najít unikátní shoda, odkaz vydá chybovou zprávu. Použití [DUMPBIN](dumpbin-reference.md) nástroj zobrazíte [dekorovaného názvu](decorated-names.md) forma identifikátoru, když je potřeba zadat do propojovacího programu.

> [!NOTE]
> Nezadávejte upravené podobě identifikátory jazyka C, které jsou deklarovány `__cdecl` nebo `__stdcall`.

Pokud je potřeba exportovat názvu nedekorovaných funkce a mají různé exporty v závislosti na konfiguraci sestavení (například v 32bitové nebo 64bitové sestavení), můžete použít různé soubory DEF pro každou konfiguraci. (Direktivy preprocesoru podmíněné nejsou povoleny v soubory DEF). Jako alternativu můžete použít `#pragma comment` direktiv před deklaraci funkce, jak je znázorněno zde, kde `PlainFuncName` je nedekorovaný název a `_PlainFuncName@4` je upravený název funkce:

```cpp
#pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
BOOL CALLBACK PlainFuncName( Things * lpParams)
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte možnost do **další možnosti** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
