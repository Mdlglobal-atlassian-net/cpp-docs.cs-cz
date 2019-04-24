---
title: Možnosti kompilátoru MSVC
ms.date: 01/29/2018
helpviewer_keywords:
- cl.exe compiler
- x86 MSVC compiler
- ARM MSVC compiler
- compiler options, C++
- x64 MSVC compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
ms.openlocfilehash: 831aade72cd728ec42aee5ef1f320deb7bdf173d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294262"
---
# <a name="compiler-options"></a>Možnosti kompilátoru

cl.exe je nástroj, který řídí Microsoft Visual C++ (MSVC) C a kompilátory jazyka C++ a propojovací program. cl.exe lze spustit pouze v operačních systémech, které podporují Microsoft Visual Studio pro Windows.

> [!NOTE]
> Tento nástroj můžete spustit pouze z příkazového řádku pro vývojáře Visual Studio. Nelze provést toto spuštění z příkazového řádku systému nebo Průzkumníka souborů. Další informace najdete v tématu [použít MSVC nástrojů z příkazového řádku](../building-on-the-command-line.md).

Kompilátory vytvářejí soubory objektů (.obj) Common Object File Format (COFF). Propojovací program vytvoří spustitelné soubory (.exe) nebo dynamické knihovny (DLL).

Všimněte si, že jsou všechny možnosti kompilátoru malá a velká písmena. Můžete použít buď lomítka (`/`) nebo pomlčky (`-`) zadat možnost kompilátoru.

Chcete-li kompilovat bez propojení, použijte [/c](c-compile-without-linking.md) možnost.

## <a name="find-a-compiler-option"></a>Najít možnost kompilátoru

K vyhledání konkrétního kompilátoru, najdete v jednom z následujících seznamů:

- [Možnosti kompilátoru (abecední pořadí)](compiler-options-listed-alphabetically.md)

- [Možnosti kompilátoru uvedené podle kategorie](compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>Zadejte možnosti kompilátoru

Téma pro každou možnost kompilátoru popisuje, jak lze nastavit ve vývojovém prostředí. Informace o určení možnosti mimo vývojové prostředí najdete tady:

- [Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)

- [Soubory příkazů CL](cl-command-files.md)

- [Proměnné prostředí CL](cl-environment-variables.md)

## <a name="related-build-tools"></a>Nástroje pro související sestavení

[Možnosti Linkeru MSVC](linker-options.md) také ovlivňují, jak je sestaven program.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k sestavení programu v jazyce C/C++](c-cpp-building-reference.md)<br/>
[CL vyvolává linker](cl-invokes-the-linker.md)
