---
title: Základní informace o generování manifestu pro programy C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
ms.openlocfilehash: 16d5efc5c5f7ce81b4b60269b0c666fd5d24266e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492529"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>Základní informace o generování manifestu pro programy C/C++

[Manifest](/windows/win32/sbscs/manifests) je dokument XML, který může být externí soubor XML nebo prostředek vložený do aplikace nebo sestavení. Manifest [izolované aplikace](/windows/win32/SbsCs/isolated-applications) se používá ke správě názvů a verzí sdílených souběžných sestavení, ke kterým by aplikace měla vytvořit vazby za běhu. Manifest souběžného sestavení určuje jeho závislosti na názvech, verzích, prostředcích a dalších sestaveních.

Existují dva způsoby, jak vytvořit manifest pro izolovanou aplikaci nebo souběžné sestavení. Nejprve může autor sestavení ručně vytvořit soubor manifestu následující pravidla a požadavky na pojmenování. Alternativně, pokud je program závislý pouze na C++ vizuálních sestaveních, jako jsou CRT, MFC, ATL nebo jiné, lze manifest vygenerovat automaticky linkerem.

Hlavičky vizuálních C++ knihoven obsahují informace o sestavení a když jsou knihovny zahrnuty v kódu aplikace, je tato informace o sestavení používána linkerem k vytvoření manifestu finálního binárního souboru. Linker nevloží soubor manifestu do binárního souboru a může vytvořit pouze manifest jako externí soubor. Použití manifestu jako externího souboru nemusí fungovat pro všechny scénáře. Například se doporučuje, aby privátní sestavení měly vložené manifesty. V sestavách na příkazovém řádku, jako jsou ty, které používají NMAKE k sestavení kódu, manifest lze vložit pomocí nástroje manifest; Další informace naleznete v tématu [generování manifestu v příkazovém řádku](manifest-generation-at-the-command-line.md). Při sestavování v aplikaci Visual Studio může být manifest vložen nastavením vlastnosti pro nástroj manifest v dialogovém okně **Vlastnosti projektu** . viz [generování manifestu v aplikaci Visual Studio](manifest-generation-in-visual-studio.md).

## <a name="see-also"></a>Viz také:

[Koncept izolovaných aplikací a souběžných sestavení](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Sestavení izolovaných aplikací C/C++ a souběžných sestavení](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
