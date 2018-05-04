---
title: /ZF (vytváření rychlejší PDB) | Microsoft Docs
ms.date: 03/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zf
dev_langs:
- C++
helpviewer_keywords:
- /Zf
- -Zf
author: corob-msft
ms.author: corob
ms.openlocfilehash: 968ce17302fa608888c7ae2fedf695946b0119bd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="zf-faster-pdb-generation"></a>/ZF (vytváření rychlejší PDB)

Minimalizace volání RPC mspdbsrv.exe povolte rychlejší vytváření PDB v paralelní sestavení.

## <a name="syntax"></a>Syntaxe

> **/Zf**

## <a name="remarks"></a>Poznámky

**/Zf** možnost umožňuje podpora kompilátoru pro rychlejší generování soubory PDB při použití [/MP (sestavení pomocí několika procesů)](mp-build-with-multiple-processes.md) možnost, nebo pokud systém sestavení (například [nástroje MSBuild ](/visualstudio/msbuild/msbuild-reference) nebo [CMake](../../ide/cmake-tools-for-visual-cpp.md)) může spustit víc cl.exe kompilátoru procesy ve stejnou dobu. Tato možnost způsobí, že kompilátoru front-end zpoždění generování indexy typu pro každý typ záznam v souboru PDB až do konce kompilace a potom požadavky je vše v jednom volání protokolu RPC do mspdbsrv.exe, místo provedení žádost RPC pro každý záznam. Podstatně tím lze vylepšit sestavení propustnost méně zatěžuje proces mspdbsrv.exe v prostředí, kde se současně spustit více procesů kompilátoru cl.exe RPC.

Protože **/Zf** možnost se vztahuje pouze na generování PDB, vyžaduje [/Zi](z7-zi-zi-debug-information-format.md) nebo [/ZI](z7-zi-zi-debug-information-format.md) možnost.

**/Zf** možnost je k dispozici od verze Visual Studio 2017 verze 15.1, kde je vypnuto ve výchozím nastavení. Od verze Visual Studio 2017 verze 15.7 Preview 3, tato možnost je na ve výchozím nastavení při **/Zi** nebo **/ZI** možnost je povolená.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Změnit **další možnosti** vlastnost, aby zahrnovala **/Zf** a potom zvolte **OK**.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru (abecední pořadí)](compiler-options-listed-alphabetically.md)<br/>
[/MP (sestavení pomocí několika procesů)](mp-build-with-multiple-processes.md)<br/>
