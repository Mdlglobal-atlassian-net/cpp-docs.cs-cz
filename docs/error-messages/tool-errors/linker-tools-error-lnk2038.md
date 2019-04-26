---
title: Chyba linkerů LNK2038
ms.date: 12/15/2017
f1_keywords:
- LNK2038
helpviewer_keywords:
- LNK2038
ms.openlocfilehash: a22b31f1ac3226271ed7ff03b5be7dad7fff6b93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298864"
---
# <a name="linker-tools-error-lnk2038"></a>Chyba linkerů LNK2038

> zjištěna neshoda pro '*název*': hodnota '*value_1*'neodpovídá hodnotě'*value_2*"v *filename.obj*

Byla zjištěna neshoda symbolu vytvořeného linkerem. Tato chyba označuje, že různé části aplikace, včetně knihoven nebo jiný objekt kódu, aby propojení aplikace, používají konfliktní definice symbolu. [Zjištění neshody](../../preprocessor/detect-mismatch.md) – Direktiva pragma se používá k definování těchto symbolů a zjišťování konfliktních hodnot.

## <a name="possible-causes-and-solutions"></a>Možné příčiny a řešení

Této chybě může dojít, když je soubor objektu v projektu je zastaralý. Před vyzkoušením dalších řešení této chyby proveďte čisté sestavení k zajištění, že objekt soubory jsou aktuální.

Visual Studio definuje následující symboly, aby se zabránilo propojení nekompatibilního kód, který může způsobit chyby za běhu nebo jiné neočekávané chování.

- `_MSC_VER` Označuje číslo hlavní verze a podverze kompilátoru Visual C++, který slouží k vytvoření aplikace nebo knihovna. Kód, který je zkompilován pomocí jedné verze kompilátoru jazyka Visual C++ není kompatibilní s kódem, který je zkompilován s použitím verzi, která má různé hlavní verze a podverze čísla. Další informace najdete v tématu `_MSC_VER` v [předdefinovaná makra](../../preprocessor/predefined-macros.md).

   Pokud odkazujete na knihovnu, která není kompatibilní s verzí kompilátoru Visual C++, který používáte, a nelze získat nebo vytvořit kompatibilní verzi knihovny, můžete použít starší verzi kompilátoru k sestavení projektu: změnit **sada nástrojů platformy** vlastnosti projektu starší sadu nástrojů. Další informace najdete v tématu [jak: Změna cílové architektury a sady nástrojů](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- `_ITERATOR_DEBUG_LEVEL` Informuje o úrovni zabezpečení a ladění funkcí, které jsou povoleny ve standardní knihovně jazyka C++. Tyto funkce mohou změnit reprezentaci některých objektů standardní knihovny C++ a tím je znekompatibilnit ty použití různých zabezpečení a ladění funkcí. Další informace najdete v tématu [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md).

- `RuntimeLibrary` Určuje verzi modulu runtime standardní knihovny C++ a C, který používá aplikace nebo knihovna. Kód, který používá jednu verzi modulu runtime standardní knihovny C++ nebo C je nekompatibilní s kódem, který používá jinou verzi. Další informace najdete v tématu [/ / MD, / MT, /LD (použití knihovny Run-Time)](../../build/reference/md-mt-ld-use-run-time-library.md).

- `_PPLTASKS_WITH_WINRT` Označuje, že kód, který používá [knihovna paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) je propojen s objekty zkompilovanými s použitím různých nastavení [/ZW](../../build/reference/zw-windows-runtime-compilation.md) – možnost kompilátoru. (**/ZW** podporuje C++/CX.) Kód, který se používá nebo závisí na PPL musí být zkompilován pomocí stejné **/ZW** nastavení, které se používá ve zbývající části aplikace.

Zajistěte, aby byly hodnoty těchto symbolů konzistentní v rámci projektů v řešení sady Visual Studio a také, že jsou slučitelné s kódem a knihovnami, které vaše aplikace připojuje.

## <a name="third-party-library-issues-and-vcpkg"></a>Problémy knihovny třetí strany a Vcpkg

Pokud tato chyba se zobrazí, když se pokoušíte nakonfigurovat knihovny třetích stran jako součást vašeho sestavení, zvažte použití [Vcpkg](../../vcpkg.md), Visual C++ balíček správce k instalaci a vytvoření knihovny. Vcpkg podporuje jejichž [seznam knihoven třetích stran](https://github.com/Microsoft/vcpkg/tree/master/ports)a nastaví vlastnosti konfigurace a závislosti, které vyžaduje pro úspěšné sestavení jako součást vašeho projektu. Další informace najdete v tématu související [blogu Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) příspěvku.

## <a name="see-also"></a>Viz také:

[Chyby a upozornění linkerů](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)