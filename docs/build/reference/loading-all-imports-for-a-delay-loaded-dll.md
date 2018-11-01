---
title: Načtení všech importů pro knihovnu DLL se zpožděným načtením
ms.date: 11/04/2016
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
ms.openlocfilehash: a9e9df6b0bae49eaf599e56e5d96040afae315e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536562"
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>Načtení všech importů pro knihovnu DLL se zpožděným načtením

**__HrLoadAllImportsForDll** funkce, která je definována v delayhlp.cpp, přikazuje linkeru, aby načtení všech importů z knihovny DLL, který byl zadán s [/delayload](../../build/reference/delayload-delay-load-import.md) – možnost linkeru.

Načtení všech importů umožňuje umístit na jednom místě v kódu pro zpracování chyb a není nutné používat kolem skutečné volání příkazu imports zpracování výjimek. Také se vyhnete situace, kdy vaše aplikace předá částečně procesem v důsledku kód pomocného objektu nedaří se načíst importu.

Volání **__HrLoadAllImportsForDll** nezmění chování hooks a Chyba zpracování; viz [zpracování chyb a oznámení](../../build/reference/error-handling-and-notification.md) Další informace.

Předaný název knihovny DLL **__HrLoadAllImportsForDll** je ve srovnání s názvem uložený v knihovně DLL a je velká a malá písmena.

Následující příklad ukazuje, jak volat **__HrLoadAllImportsForDll**:

```
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {
   printf ( "failed on snap load, exiting\n" );
   exit(2);
}
```

## <a name="see-also"></a>Viz také

[Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)