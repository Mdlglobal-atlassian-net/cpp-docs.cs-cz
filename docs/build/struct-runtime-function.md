---
title: RUNTIME_FUNCTION – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f3831dc36664c556cf0a020ed87c60200443fd3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718234"
---
# <a name="struct-runtimefunction"></a>struct RUNTIME_FUNCTION

Zpracování výjimek v tabulce vyžaduje záznam tabulky pro všechny funkce, které přidělit místo v zásobníku nebo volat jiné funkci (například úrovni funkcí). Položky tabulky funkce mají formát:

|||
|-|-|
|ULONG|Počáteční adresa – funkce|
|ULONG|Koncová adresa – funkce|
|ULONG|Adresa unwind info|

RUNTIME_FUNCTION struktura musí být typu DWORD v paměti. Všechny adresy jsou relativní bitové kopie, to znamená, jsou 32bitový posun od počáteční adresu obrázku, který obsahuje záznam tabulky funkcí. Tyto položky jsou seřazené a vložit do části .pdata bitové kopie PE32 +. Pro dynamicky generované funkcí [kompilátorů JIT] modul runtime pro podporu těchto funkcí musí použít RtlInstallFunctionTableCallback nebo RtlAddFunctionTable poskytnout tyto informace pro operační systém. Pokud tak neučiníte způsobí nespolehlivé zpracování výjimek a ladění procesů.

## <a name="see-also"></a>Viz také

[Unwind data pro zpracování výjimek, podpora ladění](../build/unwind-data-for-exception-handling-debugger-support.md)