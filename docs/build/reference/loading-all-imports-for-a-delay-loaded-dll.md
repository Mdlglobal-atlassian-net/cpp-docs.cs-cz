---
title: Načtení všech importů pro knihovnu DLL se zpožděným načtením | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29ef1c576af7930e157dafd0f57bf0b8dff49fa6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715582"
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