---
title: Omezení odloženého načítání knihoven DLL | Microsoft Docs
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
ms.openlocfilehash: 532d5ba64288fb70b19f10386186c0b520e67661
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="constraints-of-delay-loading-dlls"></a>Omezení odloženého načítání knihoven DLL
Existují omezení týkající se načítání zpoždění importy.  
  
-   Importy dat nemůže být podporováno. Alternativní řešení je explicitně zpracovávat data importovat sami pomocí `LoadLibrary` (nebo `GetModuleHandle` po víte, že pomocná načtení zpoždění načetl knihovnu DLL) a `GetProcAddress`.  
  
-   S odloženým načtením Kernel32.dll není podporována. Je nezbytné pro pomocné rutiny načtení zpoždění provést odloženým načtením této knihovny DLL.  
  
-   [Vazba](../../build/reference/binding-imports.md) položky body, které jsou předávány nepodporuje.  
  
-   Zpoždění načítání knihovny DLL nemusí vést k stejné chování procesu, pokud jsou na proces inicializacích, které se vyskytují ve vstupní bod DLL se zpožděným načtením. Další případy patří deklarováno s použitím statické TLS (lokální úložiště vláken), [__declspec(thread)](../../cpp/thread.md), které nejsou zpracovávány při načtení knihovny DLL pomocí `LoadLibrary`. Dynamické TLS, pomocí `TlsAlloc`, `TlsFree`, `TlsGetValue`, a `TlsSetValue`, je stále k dispozici pro použití v statickou nebo odloženým načtením knihovny DLL.  
  
-   Ukazatele na funkce statický (globální) by měl znovu inicializován, na importované funkce po první volání funkce. Je to proto, že první použití funkce ukazatele bude odkazovat jinou bitovou šířku.  
  
-   Neexistuje žádný způsob aktuálně zpoždění načítání pouze konkrétní postupy z knihovny DLL při použití mechanismu normální importu.  
  
-   Vlastní konvence volání (například pomocí podmínku kódy na x86 architektury) nejsou podporovány. Navíc s plovoucí desetinnou čárkou registry nejsou uloženy na jakékoli platformě. Pokud vaše vlastní pomocná rutina nebo rutiny háku používat typy s plovoucí desetinnou čárkou, potřebují k úplně uložení a obnovení stavu s plovoucí desetinnou čárkou v počítačích s volání konvence s s plovoucí desetinnou čárkou parametry registru. Buďte opatrní s odloženým načtením DLL Knihovny CRT při volání funkcí CRT, které přijímají s plovoucí desetinnou čárkou parametry v zásobníku koprocesor (NRP) ve funkci nápovědy.  
  
## <a name="see-also"></a>Viz také  
 [Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)   
 [LoadLibrary – funkce](http://msdn.microsoft.com/library/windows/desktop/ms684175.aspx)   
 [GetModuleHandle – funkce](http://msdn.microsoft.com/library/windows/desktop/ms683199.aspx)   
 [GetProcAddress – funkce](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx)   
 [TlsAlloc – funkce](http://msdn.microsoft.com/library/windows/desktop/ms686801.aspx)   
 [TlsFree – funkce](http://msdn.microsoft.com/library/windows/desktop/ms686804.aspx)   
 [TlsGetValue – funkce](http://msdn.microsoft.com/library/windows/desktop/ms686812.aspx)   
 [TlsSetValue – funkce](http://msdn.microsoft.com/library/windows/desktop/ms686818.aspx)