---
title: /ORDER (vložení funkcí v pořadí)
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLinkerTool.FunctionOrder
- /order
helpviewer_keywords:
- ORDER linker option
- -ORDER linker option
- LINK tool [C++], program optimizing
- /ORDER linker option
- LINK tool [C++], swap tuning
- paging, optimizing
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
ms.openlocfilehash: b1927ffd2efc923157fe1956fe905c939bc62719
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807881"
---
# <a name="order-put-functions-in-order"></a>/ORDER (vložení funkcí v pořadí)

Určete pořadí propojení pro samostatně zabalených funkcí (sekvence COMDAT).

## <a name="syntax"></a>Syntaxe

> **/ ORDER:\@**<em>název souboru</em>

### <a name="parameters"></a>Parametry

*Název souboru*<br/>
Textový soubor, který určuje pořadí propojení pro funkce sekvencí COMDAT.

## <a name="remarks"></a>Poznámky

**/ORDER** – možnost kompilátoru vám umožní optimalizovat vaše program stránkování seskupením společně s funkcí, které volá funkci. Můžete taky seskupit často volané funkce. Tyto techniky označované jako *swap vyladění* nebo *stránkování optimalizace*, zvýšit pravděpodobnost, že volaná funkce je v paměti, když je potřeba a nebude muset stránkování z disku.

Při kompilaci zdrojového kódu do souboru objektu poznáte kompilátoru k vložení do vlastní oddíl s názvem jednotlivých funkcí *sekvencí COMDAT*, s použitím [/Gy (povolení propojení úrovni funkcí)](gy-enable-function-level-linking.md) kompilátoru možnost. **/ORDER** – možnost linkeru přikazuje linkeru, aby umístit sekvence Comdat do spustitelné bitové kopie v pořadí, které zadáte.

Chcete-li určit pořadí, sekvencí COMDAT, vytvořte *soubor odpovědí*, textový soubor, který obsahuje seznam jednotlivých sekvencí COMDAT podle názvu, jeden pro každý řádek v pořadí, které chcete umístit linkerem. Předejte název tohoto souboru jako *filename* parametr **/ORDER** možnost. Pro funkce jazyka C++ je název COMDAT upravené podobě název funkce. Použijte nedekorovaný název funkce jazyka C, `main`, a pro C++ funkce deklarované jako `extern "C"`. Názvy funkcí a dekorované názvy jsou malá a velká písmena. Další informace o dekorovaných názvech naleznete v tématu [dekorované názvy](decorated-names.md).

Pokud chcete zjistit dekorované názvy vašich sekvence Comdat, použijte [DUMPBIN](dumpbin-reference.md) nástroje [/symboly](symbols.md) možnost v souboru objektu. Propojovací program automaticky připojí začátek podtržítko (**\_**) funkce názvy v odpovědi soubor, pokud název začíná otazníkem (**?**) nebo zavináč ( **\@**). Například pokud zdrojový soubor example.cpp, obsahuje funkce `int cpp_func(int)`, `extern "C" int c_func(int)` a `int main(void)`, příkaz `DUMPBIN /SYMBOLS example.obj` uvádí tyto dekorované názvy:

```Output
...
088 00000000 SECT1A notype ()    External     | ?cpp_func@@YAHH@Z (int __cdecl cpp_func(int))
089 00000000 SECT22 notype ()    External     | _c_func
08A 00000000 SECT24 notype ()    External     | _main
...
```

V takovém případě zadejte názvy jako `?cpp_func@@YAHH@Z`, `c_func`, a `main` v souboru odpovědí.

Pokud více než jeden **/ORDER** možnost se zobrazí v možnosti linkeru, se projeví jako poslední.

**/ORDER** zakáže přírůstkové propojení. Může se zobrazit upozornění linkeru [LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md) při zadání této možnosti je povoleno přírůstkové propojení nebo pokud jste zadali [/zi (přírůstkové PDB)](z7-zi-zi-debug-information-format.md) – možnost kompilátoru. Pokud chcete silence toto upozornění, můžete použít [/incremental: No](incremental-link-incrementally.md) – možnost linkeru vypněte přírůstkové propojení, a použít [/zi (generování souboru PDB)](z7-zi-zi-debug-information-format.md) – možnost kompilátoru ke generování souboru PDB bez přírůstkové propojení.

> [!NOTE]
> ODKAZ nelze řadit statické funkce, protože názvy statickou funkci nejsou názvy veřejných symbolů. Když **/ORDER** není zadán, linker upozornění [LNK4037](../../error-messages/tool-errors/linker-tools-warning-lnk4037.md) je vygenerována pro každý symbolů v souboru odpovědí pořadí, který je buď statický, nebo se nenašel.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **optimalizace** stránku vlastností.

1. Upravit **pořadí funkcí** vlastnost tak, aby obsahovala název souboru odpovědi.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
