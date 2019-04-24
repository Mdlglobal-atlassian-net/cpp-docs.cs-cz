---
title: Načtení všech importů pro knihovnu DLL se zpožděným načtením
ms.date: 11/04/2016
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
ms.openlocfilehash: e855b648dc7a9ee0670c3704a11aa1897a238403
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301666"
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>Načtení všech importů pro knihovnu DLL se zpožděným načtením

**__HrLoadAllImportsForDll** funkce, která je definována v delayhlp.cpp, přikazuje linkeru, aby načtení všech importů z knihovny DLL, který byl zadán s [/delayload](delayload-delay-load-import.md) – možnost linkeru.

Načtení všech importů umožňuje umístit na jednom místě v kódu pro zpracování chyb a není nutné používat kolem skutečné volání příkazu imports zpracování výjimek. Také se vyhnete situace, kdy vaše aplikace předá částečně procesem v důsledku kód pomocného objektu nedaří se načíst importu.

Volání **__HrLoadAllImportsForDll** nezmění chování hooks a Chyba zpracování; viz [zpracování chyb a oznámení](error-handling-and-notification.md) Další informace.

Předaný název knihovny DLL **__HrLoadAllImportsForDll** je ve srovnání s názvem uložený v knihovně DLL a je velká a malá písmena.

Následující příklad ukazuje, jak volat **__HrLoadAllImportsForDll**:

```
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {
   printf ( "failed on snap load, exiting\n" );
   exit(2);
}
```

## <a name="see-also"></a>Viz také:

[Podpora linkeru pro knihovny DLL s odloženým načtením](linker-support-for-delay-loaded-dlls.md)
