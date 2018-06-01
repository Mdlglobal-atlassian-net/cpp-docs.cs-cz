---
title: Upozornění linkerů Lnk4210 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4210
dev_langs:
- C++
helpviewer_keywords:
- LNK4210
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8700d9ad8eeef177de2f70f616cb0c06ba50670
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703675"
---
# <a name="linker-tools-warning-lnk4210"></a>Upozornění linkerů LNK4210

> část *části* existuje; může existuje neošetřená statické inicializátory nebo konců

## <a name="remarks"></a>Poznámky

Nějaký kód obsahuje zavedla statické inicializátory nebo konců, ale kód VCRuntime knihovny spuštění nebo jeho ekvivalent (která je potřeba spustit statické inicializátory nebo konců) není spuštěna při spuštění aplikace. Tady jsou některé příklady kódu, který vyžaduje statické inicializátory nebo konců:

- Třída globální proměnné pomocí konstruktoru, destruktor nebo tabulky virtuální funkce.

- Globální proměnné inicializován s kompilace čas konstantní.

Chcete-li tento problém vyřešit, zkuste jednu z těchto možností:

- Odeberte všechny kód s statické inicializátory.

- Nepoužívejte [/NOENTRY](../../build/reference/noentry-no-entry-point.md). Po odebrání /NOENTRY, možná budete také muset odebrat [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) z do příkazového řádku linkeru.

- Pokud vaše sestavení používá/MT, přidejte do příkazového řádku linkeru libcmt.lib, libvcruntime.lib a libucrt.lib. Pokud vaše sestavení používá /MTd, přidejte libcmtd.lib, vcruntimed.lib a libucrtd.lib.

- Při přesouvání z/CLR: pure kompilace/CLR, odeberte [/Entry](../../build/reference/entry-entry-point-symbol.md) možnost z řádku linkeru. To umožňuje inicializace CRT a povoluje statické inicializátory mají být provedeny při spuštění aplikace. **/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

[/GS](../../build/reference/gs-buffer-security-check.md) – možnost kompilátoru vyžaduje inicializace pomocí `__security_init_cookie` funkce. Tato inicializace je dostupné ve výchozím nastavení v kódu spuštění VCRuntime knihovny, který je spuštěn v `_DllMainCRTStartup`.

- Pokud váš projekt je sestaven pomocí/Entry a/Entry předaný funkci jiné než `_DllMainCRTStartup`, musí volat funkci `_CRT_INIT` inicializace CRT. Toto volání samostatně není dostatečné, pokud vaše knihovna DLL používá /GS, vyžaduje statické inicializátory nebo je volána v rámci MFC nebo ATL kód. V tématu [knihovny DLL a Visual C++ chování běhové knihovny](../../build/run-time-library-behavior.md) Další informace.

## <a name="see-also"></a>Viz také:

- [Nastavení možností linkeru](../../build/reference/setting-linker-options.md)
