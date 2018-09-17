---
title: -vmm, - vms, - vmv (obecná reprezentace) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /vms
- /vmm
- /vmv
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d4e790281cd23ba43987ec6ab003787c115150be
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701298"
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>/vmm, /vms, /vmv (obecná reprezentace)

Kdy použít [/vmb, / vmg (metoda reprezentace)](../../build/reference/vmb-vmg-representation-method.md) je zvolen jako [metoda reprezentace](../../build/reference/vmb-vmg-representation-method.md). Tyto možnosti označení model dědičnosti definice třídy není dosud došlo.

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

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[/ vmb, / vmg (metoda reprezentace)](../../build/reference/vmb-vmg-representation-method.md)
[– možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)