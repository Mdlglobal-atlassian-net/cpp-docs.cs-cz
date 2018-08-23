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
ms.openlocfilehash: 40774d6307eb9b423ebd4fd303a48acbd87eda24
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465027"
---
# <a name="constraints-of-delay-loading-dlls"></a>Omezení odloženého načítání knihoven DLL
Existují omezení týkající se načítání zpoždění importu.  
  
-   Importy dat nejde podporovat. Alternativní řešení, je explicitně zpracovávat data importovat sami pomocí `LoadLibrary` (nebo `GetModuleHandle` až budete vědět, načtení knihovny DLL odloženě zaváděné pomocné rutiny) a `GetProcAddress`.  
  
-   S odloženým načtením Kernel32.dll se nepodporuje. Tato knihovna DLL je nezbytné pro rutiny odloženě zaváděné pomocné rutiny k provádění odloženého načítání.  
  
-   [Vytvoření vazby](../../build/reference/binding-imports.md) vstupu body, které se předávají nepodporuje.  
  
-   Zpoždění načítání knihovny DLL nemusí vést stejné chování proces, pokud existují na úrovni jednotlivého procesu inicializace, které se vyskytují ve vstupní bod knihovny DLL načtené se zpožděním. Ostatní případy zahrnují deklarované pomocí statických TLS (úložiště thread local), [__declspec(thread)](../../cpp/thread.md), která není zpracována při načtení knihovny DLL pomocí `LoadLibrary`. Dynamické TLS, pomocí `TlsAlloc`, `TlsFree`, `TlsGetValue`, a `TlsSetValue`, je stále k dispozici pro použití ve statické nebo odloženě zaváděné knihovny DLL.  
  
-   Ukazatele na statické (globální) funkce by měla opakování inicializace odběrů pro importované funkce po prvním volání funkce. Je to proto, že první použití ukazatele funkce budou odkazovat na jiné bitové šířce.  
  
-   Neexistuje žádný způsob aktuálně pro odložené načítání z knihovny DLL pouze konkrétní postupy při používání mechanismu normální importu.  
  
-   Vlastní konvence volání (například pomocí podmínku kódy na x86 architektury) nejsou podporovány. Navíc s plovoucí desetinnou čárkou registrech nejsou uloženy na libovolné platformě. Používáte-li vlastní pomocná rutina nebo rutiny hook typy s plovoucí desetinnou čárkou, potřebují zcela uložit a obnovit stav s plovoucí desetinnou čárkou na počítačích s registrem konvence s plovoucí desetinnou čárkou parametry volání. Buďte opatrní odloženého načítání knihoven DLL CRT při volání funkce CRT, které přijímají parametry s plovoucí desetinnou čárkou v zásobníku koprocesor (NDP) ve funkci nápovědy.  
  
## <a name="see-also"></a>Viz také  
 [Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)   
 [LoadLibrary – funkce](http://msdn.microsoft.com/library/windows/desktop/ms684175.aspx)   
 [Funkce GetModuleHandle](http://msdn.microsoft.com/library/windows/desktop/ms683199.aspx)   
 [GetProcAddress – funkce](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx)   
 [TlsAlloc – funkce](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc)   
 [TlsFree – funkce](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsfree)   
 [TlsGetValue – funkce](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)   
 [TlsSetValue – funkce](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlssetvalue)