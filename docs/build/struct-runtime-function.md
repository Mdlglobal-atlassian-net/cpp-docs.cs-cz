---
title: struct RUNTIME_FUNCTION
ms.date: 11/04/2016
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
ms.openlocfilehash: 6b113f6cf1e9951f9e4578e15c9ed0af3d036fa6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520247"
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