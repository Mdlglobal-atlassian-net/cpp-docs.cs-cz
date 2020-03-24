---
title: Chyba linkerů LNK2038
ms.date: 12/15/2017
f1_keywords:
- LNK2038
helpviewer_keywords:
- LNK2038
ms.openlocfilehash: 45078d8e1bdbeb23dd311d915ba2cf47e42b2663
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194509"
---
# <a name="linker-tools-error-lnk2038"></a>Chyba linkerů LNK2038

> zjistila se neshoda pro:*Name*: hodnota*value_1*se neshoduje s hodnotou*value_2*v *souboru filename. obj* .

Linker zjistil neshodu symbolů. Tato chyba označuje, že různé části aplikace, včetně knihoven nebo jiného kódu objektu, na které aplikace odkazuje, používají konfliktní definice symbolu. Direktiva pragma s [neshodou detekce](../../preprocessor/detect-mismatch.md) slouží k definování takových symbolů a zjištění jejich konfliktních hodnot.

## <a name="possible-causes-and-solutions"></a>Možné příčiny a řešení

K této chybě může dojít, pokud je soubor objektu v projektu zastaralý. Předtím, než se pokusíte o tuto chybu, proveďte čisté sestavení, aby se zajistilo, že jsou soubory objektů aktuální.

Visual Studio definuje následující symboly, aby nedocházelo k propojení nekompatibilního kódu, který může způsobit chyby za běhu nebo jiné neočekávané chování.

- `_MSC_VER` označuje číslo hlavní verze a podverze kompilátoru Microsoft C++ (MSVC), které se používají k sestavení aplikace nebo knihovny. Kód, který je zkompilován pomocí jedné verze MSVC, je nekompatibilní s kódem, který je zkompilován pomocí verze, která má odlišná čísla hlavní verze a podverze. Další informace najdete v tématu `_MSC_VER` v [předdefinovaných makrech](../../preprocessor/predefined-macros.md).

   Pokud propojujete knihovnu, která není kompatibilní s verzí MSVC, kterou používáte, a nelze získat nebo sestavit kompatibilní verzi knihovny, můžete použít starší verzi kompilátoru pro sestavení projektu: Změňte vlastnost **Sada nástrojů platformy** projektu na předchozí sadu nástrojů. Další informace naleznete v tématu [Postupy: Změna cílové architektury a sady nástrojů platformy](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- `_ITERATOR_DEBUG_LEVEL` označuje úroveň zabezpečení a funkce ladění, které jsou povoleny ve C++ standardní knihovně. Tyto funkce mohou změnit reprezentace určitých C++ objektů knihovny Standard a tak je nekompatibilní s možnostmi, které používají jiné funkce zabezpečení a ladění. Další informace najdete v tématu [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md).

- `RuntimeLibrary` označuje verzi knihovny C++ Standard a modulu runtime jazyka C, kterou používá aplikace nebo knihovna. Kód, který používá jednu verzi C++ standardní knihovny nebo modulu runtime jazyka C, není kompatibilní s kódem, který používá jinou verzi. Další informace naleznete v tématu [/MD,/MT,/LD (použití běhové knihovny)](../../build/reference/md-mt-ld-use-run-time-library.md).

- `_PPLTASKS_WITH_WINRT` označuje, že kód, který používá [knihovnu paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) , je propojen s objekty kompilovány pomocí jiného nastavení pro možnost kompilátoru [/ZW](../../build/reference/zw-windows-runtime-compilation.md) . ( **/ZW** podporuje C++/CX.) Kód, který používá nebo závisí na PPL, musí být kompilován pomocí stejného nastavení **/ZW** , které se používá ve zbývající části aplikace.

Zajistěte, aby hodnoty těchto symbolů byly konzistentní v rámci projektů v řešení sady Visual Studio a také byly konzistentní s kódem a knihovnami, na které vaše aplikace odkazuje.

## <a name="third-party-library-issues-and-vcpkg"></a>Problémy s knihovnou třetích stran a Vcpkg

Pokud se tato chyba zobrazí při pokusu o konfiguraci knihovny třetí strany v rámci sestavení, zvažte použití [Vcpkg](../../vcpkg.md), správce balíčků Visual C++ , k instalaci a sestavení knihovny. Vcpkg podporuje velký a rostoucí [seznam knihoven třetích stran](https://github.com/Microsoft/vcpkg/tree/master/ports)a nastavuje všechny vlastnosti konfigurace a závislosti vyžadované pro úspěšná sestavení v rámci projektu. Další informace najdete v souvisejícím [ C++ blogovém](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) příspěvku.

## <a name="see-also"></a>Viz také

[Chyby a upozornění linkerů](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
