---
title: / VMM, - vms, - vmv (obecná reprezentace)
ms.date: 11/04/2016
f1_keywords:
- /vms
- /vmm
- /vmv
helpviewer_keywords:
- Virtual Inheritance compiler option
- general purpose representation compiler options
- vms compiler option [C++]
- vmm compiler option [C++]
- /vmm compiler option [C++]
- -vmm compiler option [C++]
- -vms compiler option [C++]
- /vms compiler option [C++]
- vmv compiler option [C++]
- /vmv compiler option [C++]
- Single Inheritance compiler option
- -vmv compiler option [C++]
ms.assetid: 0fcd7ae0-3031-4c62-a2a8-e154c8685dae
ms.openlocfilehash: 7a46cecdbf96ad891ce218df4769a60590e562a9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810039"
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>/vmm, /vms, /vmv (obecná reprezentace)

Kdy použít [/vmb, / vmg (metoda reprezentace)](vmb-vmg-representation-method.md) je zvolen jako [metoda reprezentace](vmb-vmg-representation-method.md). Tyto možnosti označení model dědičnosti definice třídy není dosud došlo.

## <a name="syntax"></a>Syntaxe

```
/vmm
/vms
/vmv
```

## <a name="remarks"></a>Poznámky

Tyto možnosti jsou popsány v následující tabulce.

|Možnost|Popis|
|------------|-----------------|
|**/vmm**|Určuje nejobecnější reprezentace ukazatele na člen třídy bude ten, který se používá vícenásobné dědičnosti.<br /><br /> Odpovídající [– klíčové slovo dědičnosti](../../cpp/inheritance-keywords.md) a argument [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) je **vícenásobná dědičnost –**.<br /><br /> Tento zápis je větší než požadované pro jednoduchou dědičnost.<br /><br /> Pokud je model dědičnosti definice třídy, pro kterou je ukazatel na člen deklarován jako virtuální, kompilátor vygeneruje chybu.|
|**/vms**|Určuje nejobecnější reprezentace ukazatele na člen třídy bude ten, který používá žádné dědičnosti nebo jednoduchá dědičnost.<br /><br /> Odpovídající [– klíčové slovo dědičnosti](../../cpp/inheritance-keywords.md) a argument [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) je **single_inheritance**.<br /><br /> Toto je nejmenší možnou reprezentaci ukazatele na člen třídy.<br /><br /> Pokud je model dědičnosti definice třídy, pro kterou je ukazatel na člen deklarován jako více nebo virtuální, kompilátor vygeneruje chybu.|
|**/vmv**|Určuje nejobecnější reprezentace ukazatele na člen třídy bude ten, který používá virtuální dědičnost. Nikdy způsobí chybu a je výchozí nastavení.<br /><br /> Odpovídající [– klíčové slovo dědičnosti](../../cpp/inheritance-keywords.md) a argument [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) je **virtual_inheritance**.<br /><br /> Tato možnost vyžaduje větší ukazatele a dalšího kódu k interpretaci tohoto ukazatele než u ostatních možností.|

Pokud chcete zadat jednu z těchto možností model dědičnosti, tohoto modelu se používá pro všechny ukazatele na členy třídy, bez ohledu na jejich typ dědičnosti nebo zda ukazatel je deklarován před nebo po třídy. Proto pokud vždy používáte jednoduché dědičnosti tříd, můžete snížit velikost kódu kompilaci **/VMS**; nicméně, pokud chcete mít nejobecnější velikost (za cenu největší reprezentaci dat), proveďte kompilaci s **/vmv**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[/vmb, /vmg (metoda reprezentace)](vmb-vmg-representation-method.md)<br/>
[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
