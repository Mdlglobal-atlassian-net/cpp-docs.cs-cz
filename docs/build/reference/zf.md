---
title: /ZF (rychlejší generování souborů PDB)
ms.date: 03/29/2018
f1_keywords:
- /Zf
helpviewer_keywords:
- /Zf
- -Zf
ms.openlocfilehash: bed37a189e3eb1eb7b55dbdee1f81f360eafa721
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814043"
---
# <a name="zf-faster-pdb-generation"></a>/ZF (rychlejší generování souborů PDB)

Povolte rychlejší generování souborů PDB v paralelních sestaveních minimalizací volání RPC mspdbsrv.exe.

## <a name="syntax"></a>Syntaxe

> **/Zf**

## <a name="remarks"></a>Poznámky

**/Zf** možnost umožňuje podporu kompilátoru pro rychlejší generování souborů PDB při použití [/MP (sestavení pomocí několika procesů)](mp-build-with-multiple-processes.md) možnost, nebo když systém sestavení (například [MSBuild ](/visualstudio/msbuild/msbuild-reference) nebo [CMake](../cmake-projects-in-visual-studio.md)) může spouštět více cl.exe kompilátoru procesy ve stejnou dobu. Tato možnost způsobí, že kompilátor front-endu pro odložené generování indexů typu. pro každý typ záznam do souboru PDB až do konce kompilace a vyžádá všechno v jednom volání RPC do mspdbsrv.exe místo provedení požadavek RPC pro každý záznam. Podstatně tím lze vylepšit vysokou propustnost sestavování snižování zatížení protokolu RPC procesu mspdbsrv.exe v prostředí, kde více procesů kompilátor cl.exe spouštět souběžně.

Vzhledem k tomu, **/Zf** možnost se vztahuje pouze na generování souborů PDB, vyžaduje [/zi](z7-zi-zi-debug-information-format.md) nebo [/zi](z7-zi-zi-debug-information-format.md) možnost.

**/Zf** možnost je k dispozici od verze Visual Studio 2017 verze 15.1, kde je vypnuto ve výchozím nastavení. Spouští se v sadě Visual Studio 2017 verze 15.7 ve verzi Preview 3, tato možnost zapnutá ve výchozím nastavení při **/zi** nebo **/zi** je povolená možnost.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/Zf** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru (abecední pořadí)](compiler-options-listed-alphabetically.md)<br/>
[/MP (sestavení pomocí několika procesů)](mp-build-with-multiple-processes.md)<br/>
