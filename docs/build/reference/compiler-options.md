---
title: Možnosti kompilátoru | Dokumentace Microsoftu
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
ms.openlocfilehash: 76ab322dc4573863a30092b296e87e90c41619ab
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716207"
---
# <a name="compiler-options"></a>Možnosti kompilátoru

cl.exe je nástroj, který řídí Microsoft Visual C++ (MSVC) C a kompilátory jazyka C++ a propojovací program. cl.exe lze spustit pouze v operačních systémech, které podporují Microsoft Visual Studio pro Windows.

> [!NOTE]
> Tento nástroj můžete spustit pouze z příkazového řádku pro vývojáře Visual Studio. Nelze provést toto spuštění z příkazového řádku systému nebo Průzkumníka souborů. Další informace najdete v tématu [kódu sestavení C/C++ v příkazovém řádku](../building-on-the-command-line.md).

Kompilátory vytvářejí soubory objektů (.obj) Common Object File Format (COFF). Propojovací program vytvoří spustitelné soubory (.exe) nebo dynamické knihovny (DLL).

Všimněte si, že jsou všechny možnosti kompilátoru malá a velká písmena. Můžete použít buď lomítka (`/`) nebo pomlčky (`-`) zadat možnost kompilátoru.

Chcete-li kompilovat bez propojení, použijte [/c](../../build/reference/c-compile-without-linking.md) možnost.

## <a name="find-a-compiler-option"></a>Najít možnost kompilátoru

K vyhledání konkrétního kompilátoru, najdete v jednom z následujících seznamů:

- [Možnosti kompilátoru (abecední pořadí)](../../build/reference/compiler-options-listed-alphabetically.md)

- [Možnosti kompilátoru uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>Zadejte možnosti kompilátoru

Téma pro každou možnost kompilátoru popisuje, jak lze nastavit ve vývojovém prostředí. Informace o určení možnosti mimo vývojové prostředí najdete tady:

- [Syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md)

- [Soubory příkazů CL](../../build/reference/cl-command-files.md)

- [Proměnné prostředí CL](../../build/reference/cl-environment-variables.md)

## <a name="related-build-tools"></a>Nástroje pro související sestavení

[Možnosti linkeru](../../build/reference/linker-options.md) také ovlivňují, jak je sestaven program.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k sestavení programu v jazyce C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[Rychlá kompilace](../../build/reference/fast-compilation.md)<br/>
[CL vyvolává linker](../../build/reference/cl-invokes-the-linker.md)
