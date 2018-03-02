---
title: "/ZF (vytváření rychlejší PDB) | Microsoft Docs"
ms.date: 02/22/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /Zf
dev_langs:
- C++
helpviewer_keywords:
- /Zf
- -Zf
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e8817b72e5e6eb7ba808455113104e8fb5000505
ms.sourcegitcommit: d24de38f9da844f824acb9d200a3f263077145fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="zf-faster-pdb-generation"></a>/ZF (vytváření rychlejší PDB)

Minimalizace volání RPC mspdbsrv.exe povolte rychlejší vytváření PDB v paralelní sestavení.

## <a name="syntax"></a>Syntaxe

> **/Zf**

## <a name="remarks"></a>Poznámky

**/Zf** možnost umožňuje podpora kompilátoru pro rychlejší generování soubory PDB při použití [/MP (sestavení pomocí několika procesů)](mp-build-with-multiple-processes.md) možnost, nebo pokud systém sestavení (například [nástroje MSBuild ](/visualstudio/msbuild/msbuild-reference) nebo [CMake](../../ide/cmake-tools-for-visual-cpp.md)) může spustit víc cl.exe kompilátoru procesy ve stejnou dobu. Tato možnost způsobí, že kompilátoru front-end zpoždění generování indexy typu pro každý typ záznam v souboru PDB až do konce kompilace a potom požadavky je vše v jednom volání protokolu RPC do mspdbsrv.exe, místo provedení žádost RPC pro každý záznam. Podstatně tím lze vylepšit sestavení propustnost méně zatěžuje proces mspdbsrv.exe v prostředí, kde se současně spustit více procesů kompilátoru cl.exe RPC.

Protože **/Zf** možnost se vztahuje pouze na generování PDF, vyžaduje [/Zi](z7-zi-zi-debug-information-format.md) nebo [/ZI](z7-zi-zi-debug-information-format.md) možnost.

**/Zf** možnost je k dispozici od verze Visual Studio 2017 verze 15.1 a ve výchozím nastavení.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Změnit **další možnosti** vlastnost, aby zahrnovala **/Zf** a potom zvolte **OK**.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru (abecední pořadí)](compiler-options-listed-alphabetically.md)  
[/MP (sestavení pomocí několika procesů)](mp-build-with-multiple-processes.md)  
