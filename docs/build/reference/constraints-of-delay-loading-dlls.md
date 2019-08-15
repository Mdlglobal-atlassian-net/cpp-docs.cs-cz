---
title: Omezení odloženého načítání knihoven DLL
ms.date: 11/04/2016
helpviewer_keywords:
- constraints [C++], delayed loading of DLLs
- delayed loading of DLLs, constraints
- DLLs [C++], constraints
ms.assetid: 0097ff65-550f-4a4e-8ac3-39bf6404f926
ms.openlocfilehash: be5e5eb360f80e0b2ea9682f38f6787044cd3c63
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493071"
---
# <a name="constraints-of-delay-loading-dlls"></a>Omezení odloženého načítání knihoven DLL

Existují omezení týkající se opožděného načítání importů.

- Import dat nelze podporovat. Alternativním řešením je explicitně zpracovat import dat pomocí `LoadLibrary` (nebo `GetModuleHandle` po zjištění, že pomocník pro zpožděné načítání načetl knihovnu DLL) a `GetProcAddress`.

- Zpožděné načítání Kernel32. dll se nepodporuje. Tato knihovna DLL je nezbytná pro pomocné rutiny pro zpožděné načtení k provedení zpožděného načtení.

- [Vazba](binding-imports.md) vstupních bodů, které jsou předávány, není podporována.

- Zpožděné načítání knihoven DLL nemusí mít za následek stejné chování procesu, pokud dojde k inicializaci jednotlivých procesů, ke kterým dochází v vstupním bodě knihovny DLL s odloženým načtením. Jiné případy zahrnují statický protokol TLS (thread local Storage) deklarovaný pomocí [__declspec (thread)](../../cpp/thread.md), který se nezpracovává při načtení knihovny DLL prostřednictvím `LoadLibrary`. Dynamické TLS, použití `TlsAlloc`, `TlsFree`, `TlsGetValue` `TlsSetValue`a, je stále k dispozici pro použití buď v statických, nebo ve zpožděně načtených knihovnách DLL.

- Po prvním volání funkce by měly být do importovaných funkcí znovu inicializovány ukazatele na statických (globálních) funkcích. Je to proto, že první použití ukazatele na funkci odkazuje na převedené volání.

- V současné době neexistuje způsob, jak zpozdit načítání pouze konkrétních postupů z knihovny DLL při použití normálního mechanismu importu.

- Vlastní konvence volání (například použití kódů podmínek u architektur x86) nejsou podporovány. Také Registry s plovoucí desetinnou čárkou nejsou uloženy na žádné platformě. Pokud vlastní rutina pomocné rutiny nebo rutiny vidlice používají typy s plovoucí desetinnou čárkou, musí na počítačích kompletně ukládat a obnovovat stav s plovoucí desetinnou čárkou s použitím parametrů s plovoucí desetinnou čárkou. Pokud voláte funkce CRT, které v zásobníku NDP (numerický datový procesor) využívají v rámci funkce Help rozhraní s plovoucí desetinnou čárkou, buďte opatrní na zpoždění načítání knihovny DLL CRT.

## <a name="see-also"></a>Viz také:

[Podpora linkeru pro knihovny DLL s odloženým načtením](linker-support-for-delay-loaded-dlls.md)<br/>
[LoadLibrary – funkce](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)<br/>
[GetModuleHandle – funkce](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlew)<br/>
[GetProcAddress – funkce](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)<br/>
[TlsAlloc – funkce](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)<br/>
[TlsFree – – funkce](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsfree)<br/>
[TlsGetValue – funkce](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)<br/>
[TlsSetValue – funkce](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlssetvalue)
