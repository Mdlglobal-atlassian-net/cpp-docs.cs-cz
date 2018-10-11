---
title: Omezení odloženého načítání knihoven DLL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- constraints [C++], delayed loading of DLLs
- delayed loading of DLLs, constraints
- DLLs [C++], constraints
ms.assetid: 0097ff65-550f-4a4e-8ac3-39bf6404f926
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 497de9695e75810f2fe68101627f2ba3606aa048
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082006"
---
# <a name="constraints-of-delay-loading-dlls"></a>Omezení odloženého načítání knihoven DLL

Existují omezení týkající se načítání zpoždění importu.

- Importy dat nejde podporovat. Alternativní řešení, je explicitně zpracovávat data importovat sami pomocí `LoadLibrary` (nebo `GetModuleHandle` až budete vědět, načtení knihovny DLL odloženě zaváděné pomocné rutiny) a `GetProcAddress`.

- S odloženým načtením Kernel32.dll se nepodporuje. Tato knihovna DLL je nezbytné pro rutiny odloženě zaváděné pomocné rutiny k provádění odloženého načítání.

- [Vytvoření vazby](../../build/reference/binding-imports.md) vstupu body, které se předávají nepodporuje.

- Zpoždění načítání knihovny DLL nemusí vést stejné chování proces, pokud existují na úrovni jednotlivého procesu inicializace, které se vyskytují ve vstupní bod knihovny DLL načtené se zpožděním. Ostatní případy zahrnují deklarované pomocí statických TLS (úložiště thread local), [__declspec(thread)](../../cpp/thread.md), která není zpracována při načtení knihovny DLL pomocí `LoadLibrary`. Dynamické TLS, pomocí `TlsAlloc`, `TlsFree`, `TlsGetValue`, a `TlsSetValue`, je stále k dispozici pro použití ve statické nebo odloženě zaváděné knihovny DLL.

- Ukazatele na statické (globální) funkce by měla opakování inicializace odběrů pro importované funkce po prvním volání funkce. Je to proto, že první použití ukazatele funkce budou odkazovat na jiné bitové šířce.

- Neexistuje žádný způsob aktuálně pro odložené načítání z knihovny DLL pouze konkrétní postupy při používání mechanismu normální importu.

- Vlastní konvence volání (například pomocí podmínku kódy na x86 architektury) nejsou podporovány. Navíc s plovoucí desetinnou čárkou registrech nejsou uloženy na libovolné platformě. Používáte-li vlastní pomocná rutina nebo rutiny hook typy s plovoucí desetinnou čárkou, potřebují zcela uložit a obnovit stav s plovoucí desetinnou čárkou na počítačích s registrem konvence s plovoucí desetinnou čárkou parametry volání. Buďte opatrní odloženého načítání knihoven DLL CRT při volání funkce CRT, které přijímají parametry s plovoucí desetinnou čárkou v zásobníku koprocesor (NDP) ve funkci nápovědy.

## <a name="see-also"></a>Viz také

[Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)<br/>
[LoadLibrary – funkce](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya)<br/>
[Funkce GetModuleHandle](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulehandlea)<br/>
[GetProcAddress – funkce](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress)<br/>
[TlsAlloc – funkce](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc)<br/>
[TlsFree – funkce](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsfree)<br/>
[TlsGetValue – funkce](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)<br/>
[TlsSetValue – funkce](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlssetvalue)