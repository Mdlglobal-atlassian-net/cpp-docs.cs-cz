---
title: Chyba linkerů Lnk2038 | Microsoft Docs
ms.custom: ''
ms.date: 12/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2038
dev_langs:
- C++
helpviewer_keywords:
- LNK2038
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f97f65bbe31e51e5083b34949b47a6963696ee37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301665"
---
# <a name="linker-tools-error-lnk2038"></a>Chyba linkerů LNK2038

> zjištěna neshoda u '*název*': hodnota se*value_1*'neodpovídá hodnota'*value_2*' v *filename.obj*

Byla zjištěna neshoda symbol podle linkeru. Tato chyba znamená, že různé části aplikace, včetně knihovny nebo jiného objektu code, odkazy aplikace, použít konfliktní definice symbolu. [Zjistit neshoda](../../preprocessor/detect-mismatch.md) – Direktiva pragma se používá k definování takových symbolů a zjistit jejich konfliktní hodnoty.

## <a name="possible-causes-and-solutions"></a>Možné příčiny a řešení

Této chybě může dojít, když je zastaralý. soubor objektu ve vašem projektu. Než se pokusíte další řešení této chyby, vytvořit nové čisté sestavení zajistit, že objekt soubory jsou aktuální.

Visual Studio definuje následující symboly, aby se zabránilo propojení nekompatibilní kód, který může způsobit chyby nebo další neočekávanému chování.

- `_MSC_VER`  
   Určuje počet hlavní verze a podverze – kompilátor Visual C++, který je použit k vytvoření aplikace nebo knihovny. Kód, který je sestaven pomocí jednu verzi Visual C++ compiler není kompatibilní s kód, který je sestaven pomocí na verzi, která má jiný hlavní verze a podverze čísla. Další informace najdete v tématu `_MSC_VER` v [předdefinovaná makra](../../preprocessor/predefined-macros.md).

   Pokud vytváříte odkaz na knihovnu, která není kompatibilní s verzí aplikace Visual C++ compiler, který používáte, a nelze získat nebo sestavení kompatibilní verzi knihovny, můžete použít starší verzi kompilátor k sestavení projektu: změnit <C1/>sada nástrojů platformy** vlastnost projekt starší nástrojů. Další informace najdete v tématu [postupy: Změna cílové architektury a sady nástrojů](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- `_ITERATOR_DEBUG_LEVEL`  
   Určuje úroveň zabezpečení a ladění funkcí, které jsou povoleny ve standardní knihovně C++. Tyto funkce můžete změnit reprezentace objektů určité standardní knihovna C++ a tím je provést nekompatibilní s těmi, že použití různých zabezpečení a ladění funkcí. Další informace najdete v tématu [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md).

- `RuntimeLibrary`  
   Určuje verzi standardní knihovna C++ a C runtime, který se používá aplikaci nebo knihovny. Kód, který používá jednu verzi modulu runtime standardní knihovna C++ nebo C je nekompatibilní s kódem, který používá jinou verzi. Další informace najdete v tématu [/MD, / MT, /LD (použít běhovou knihovnu)](../../build/reference/md-mt-ld-use-run-time-library.md).

- `_PPLTASKS_WITH_WINRT`  
   Určuje, že kód, který používá [paralelní vzory knihovna PPL ()](../../parallel/concrt/parallel-patterns-library-ppl.md) je propojená s objekty zkompilovat pomocí různých nastavení [/ZW](../../build/reference/zw-windows-runtime-compilation.md) – možnost kompilátoru. (**/ZW** podporuje C + +/ CX.) Kód, který používá nebo závisí na knihovně PPL musí být zkompilovány pomocí stejné **/ZW** nastavení, která se používá ve zbývající části aplikace.

Ujistěte se, že hodnoty tyto symboly jsou konzistentní v rámci projekty v řešení sady Visual Studio a také, zda jsou konzistentní s kódem a knihovny, které vaše aplikace odkazuje na.

## <a name="third-party-library-issues-and-vcpkg"></a>Knihovna třetích stran problémy a Vcpkg

Pokud se zobrazí tato chyba, když se pokoušíte nakonfigurovat jako součást buildu knihovnu třetích stran, zvažte použití [Vcpkg](../../vcpkg.md), Visual C++ Package Manager k instalaci a sestavení knihovny. Vcpkg podporuje velkou a rostoucí [seznam knihoven jiných výrobců](https://github.com/Microsoft/vcpkg/tree/master/ports)a nastaví vlastnosti konfigurace a závislosti v rámci projektu požadované pro úspěšné sestavení. Další informace najdete v tématu související [Visual C++ Blog](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) post.

## <a name="see-also"></a>Viz také

[Chyby a upozornění linkerů](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)