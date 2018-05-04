---
title: Možnosti kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler
- x86 Visual C++ compiler
- ARM Visual C++ compiler
- compiler options, C++
- x64 Visual C++ compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bea07361a292ee5e7cde99cedad2d5ac4c8a53aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="compiler-options"></a>Možnosti kompilátoru

cl.exe je nástroj, který řídí Microsoft Visual C++ (MSVC) C a C++ kompilátory a linkeru. cl.exe lze spustit pouze v operačních systémech, které podporují Microsoft Visual Studio pro Windows.

> [!NOTE]  
> Tento nástroj můžete spustit pouze z příkazového řádku vývojáře Visual Studio. Nelze ji spustit z příkazového řádku systému nebo v Průzkumníku souborů. Další informace najdete v tématu [kódu sestavení C/C++ v příkazovém řádku](../building-on-the-command-line.md).

Kompilátory vytvořit soubory objektů (.obj) běžné objekt souboru formátu (COFF). Spustitelné soubory (.exe) nebo dynamické knihovny (DLL), který produkuje linkeru.

Všimněte si, že jsou všechny možnosti kompilátoru velká a malá písmena. Můžete použít buď lomítkem (`/`) nebo pomlčkou (`-`) k určení možnost kompilátoru.

Chcete-li kompilovat bez propojení, použijte [/c](../../build/reference/c-compile-without-linking.md) možnost.

## <a name="find-a-compiler-option"></a>Najít – možnost kompilátoru

Možnost konkrétní kompilátoru naleznete v tématu jednu z následujících seznamů:

- [Možnosti kompilátoru (abecední pořadí)](../../build/reference/compiler-options-listed-alphabetically.md)

- [Možnosti kompilátoru uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>Zadejte možnosti kompilátoru

Téma pro každý – možnost kompilátoru popisuje, jak lze nastavit ve vývojovém prostředí. Informace o zadání možností mimo vývojového prostředí najdete v tématu:

- [Syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md)

- [Soubory příkazů CL](../../build/reference/cl-command-files.md)

- [Proměnné prostředí CL](../../build/reference/cl-environment-variables.md)

## <a name="related-build-tools"></a>Související sestavovací nástroje

[Možnosti linkeru](../../build/reference/linker-options.md) ovlivní také, jak je integrovaná vašeho programu.

## <a name="see-also"></a>Viz také

[Referenční zdroje k sestavení programu v jazyce C/C++](../../build/reference/c-cpp-building-reference.md)  
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)  
[Rychlá kompilace](../../build/reference/fast-compilation.md)  
[CL vyvolává linker](../../build/reference/cl-invokes-the-linker.md)  
