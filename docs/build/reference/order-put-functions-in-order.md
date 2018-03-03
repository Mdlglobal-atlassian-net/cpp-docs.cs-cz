---
title: "-ORDER (vložení funkcí v pořadí) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.FunctionOrder
- /order
dev_langs:
- C++
helpviewer_keywords:
- ORDER linker option
- -ORDER linker option
- LINK tool [C++], program optimizing
- /ORDER linker option
- LINK tool [C++], swap tuning
- paging, optimizing
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2264296d288f9105a59c0ac5099c1dedef55ee2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="order-put-functions-in-order"></a>/ORDER (vložení funkcí v pořadí)

Určete pořadí propojení pro samostatně zabalené funkce (sekvence COMDAT).

## <a name="syntax"></a>Syntaxe

>/ POŘADÍ: @*filename*

### <a name="parameters"></a>Parametry

*Název souboru*  
Textový soubor, který určuje pořadí propojení pro sekvence COMDAT funkce.

## <a name="remarks"></a>Poznámky

**/Pořadí** – možnost kompilátoru umožňuje optimalizovat chování stránkování vašeho programu tím, že funkce společně s funkcí zavolá. Můžete taky seskupit často volaných funkcí. Tyto postupy, označuje jako *swap vyladění* nebo *stránkování optimalizace*, zvýšit pravděpodobnost, že volaná funkce je v paměti, pokud je potřeba a nemá být stránkovaného fondu z disku.

Při kompilaci zdrojového kódu do souboru objektu, se dá zjistit kompilátoru převést jednotlivé funkce do vlastní oddíl s názvem *sekvence COMDAT*, pomocí [/Gy (povolení propojení na úrovni funkcí)](../../build/reference/gy-enable-function-level-linking.md) kompilátoru možnost. **/Pořadí** – možnost linkeru informuje linkeru COMDATs umístit do spustitelné bitové kopie v pořadí, které zadáte.

Chcete-li určit pořadí, sekvence COMDAT, vytvořte *soubor odezvy*, textový soubor, který uvádí každý sekvence COMDAT podle názvu, jeden na každý řádek v pořadí, které mají být umístěny ve linkeru. Předat název tento soubor jako *filename* parametr **/pořadí** možnost. Pro funkcí jazyka C++ je název sekvence COMDAT dekorované formu název funkce. Používejte pro funkce C upraveného název `main`, a pro funkcí jazyka C++ deklarován jako `extern "C"`. Názvy funkcí a dekorované názvy jsou velká a malá písmena. Další informace o dekorovaných názvech najdete v tématu [dekorované názvy](../../build/reference/decorated-names.md). 

K vyhledání dekorované názvy vaší COMDATs, použijte [DUMPBIN](../../build/reference/dumpbin-reference.md) nástroje [/symboly](../../build/reference/symbols.md) možnost na soubor objektu. Linkeru automaticky přidá podtržítko (\_) funkce názvy v odpovědi soubor, pokud název spustí s otazníkem (?) nebo znaku zavináče (@). Například pokud zdrojový soubor example.cpp, obsahuje funkce `int cpp_func(int)`, `extern "C" int c_func(int)` a `int main(void)`, příkaz `DUMPBIN /SYMBOLS example.obj` uvádí tyto dekorované názvy:

```Output
...
088 00000000 SECT1A notype ()    External     | ?cpp_func@@YAHH@Z (int __cdecl cpp_func(int))
089 00000000 SECT22 notype ()    External     | _c_func
08A 00000000 SECT24 notype ()    External     | _main
...
```

V takovém případě zadejte názvy jako `?cpp_func@@YAHH@Z`, `c_func`, a `main` v souboru odpovědí.

Pokud je více než jeden **/pořadí** možnost se zobrazí v možnosti linkeru, byl naposledy projeví.

**/Pořadí** možnost zakáže přírůstkové propojování. Může se zobrazit upozornění linkerů [LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md) Pokud zadáte tuto možnost pokud přírůstkové propojování je povoleno, nebo pokud jste zadali [/ZI (přírůstkové PDB)](../../build/reference/z7-zi-zi-debug-information-format.md) – možnost kompilátoru. K silence toto upozornění, můžete použít [/INCREMENTAL:NO](../../build/reference/incremental-link-incrementally.md) – možnost linkeru vypněte přírůstkové propojování a použít [/Zi (Generovat PDB)](../../build/reference/z7-zi-zi-debug-information-format.md) – možnost kompilátoru ke generování PDB bez přírůstkové propojování.

> [!NOTE]
> ODKAZ nelze pořadí statické funkce, protože nejsou statické funkce názvy názvy veřejných symbolů. Když **/pořadí** není zadaný, upozornění linkerů [LNK4037](../../error-messages/tool-errors/linker-tools-warning-lnk4037.md) se vygeneruje pro každý symbol v souboru odpovědí pořadí, která jsou statická nebo nebyl nalezen.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  

1. V části **vlastnosti konfigurace**, otevřete **Linkeru** a potom zvolte **optimalizace** stránku vlastností.

1. Změnit **funkce pořadí** vlastnost, která má obsahovat název souboru odpovědí.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)  
[Možnosti linkeru](../../build/reference/linker-options.md)