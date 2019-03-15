---
title: Upozornění linkerů LNK4210
ms.date: 11/04/2016
f1_keywords:
- LNK4210
helpviewer_keywords:
- LNK4210
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
ms.openlocfilehash: 75376129ce0033c717a4da3074cee9de132d357d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816266"
---
# <a name="linker-tools-warning-lnk4210"></a>Upozornění linkerů LNK4210

> část *části* existuje; možná existuje neošetřené statické inicializátory nebo Terminátory

## <a name="remarks"></a>Poznámky

Nějaký kód je zavedena statické inicializátory nebo Terminátory, ale VCRuntime spouštěcí kód knihovny nebo jeho ekvivalent (který je potřeba spustit statické inicializátory nebo Terminátory) není spuštěna při spuštění aplikace. Tady jsou některé příklady kódu, který vyžaduje statické inicializátory nebo Terminátory:

- Třída globální proměnná se konstruktor, destruktor nebo virtuální tabulky funkcí.

- Globální proměnná inicializována s konstantou kompilace času.

Chcete-li tento problém vyřešit, zkuste použijte jeden z následujících akcí:

- Odeberte veškerý kód se statické inicializátory.

- Nepoužívejte [NOENTRY](../../build/reference/noentry-no-entry-point.md). Po odebrání NOENTRY budete také muset odebrat [: / NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) z příkazového řádku linkeru.

- Pokud sestavení využívá/MT, přidejte libcmt.lib libvcruntime.lib a libucrt.lib do příkazového řádku linkeru. Pokud sestavení využívá/MTD, přidejte libcmtd.lib vcruntimed.lib a libucrtd.lib.

- Při přechodu z/CLR: pure kompilace/CLR, odeberte [/Entry](../../build/reference/entry-entry-point-symbol.md) možnost z řádku linkeru. To umožňuje inicializace CRT a povoluje statické inicializátory, který se spustí při spuštění aplikace. **/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

[/GS](../../build/reference/gs-buffer-security-check.md) – možnost kompilátoru vyžaduje inicializace `__security_init_cookie` funkce. Tato inicializace je k dispozici ve výchozím nastavení v VCRuntime spouštěcí kód knihovny, na kterém běží v `_DllMainCRTStartup`.

- Pokud váš projekt se vytvořil pomocí/Entry a/Entry je předán funkci jiných než `_DllMainCRTStartup`, musí volat funkci `_CRT_INIT` inicializace CRT. Toto volání samostatně není dostatečné, pokud vaše knihovna DLL používá /GS, vyžaduje statické inicializátory nebo je volána v rámci MFC nebo ATL kód. V tématu [Visual C++ a knihoven DLL knihovny run-time chování](../../build/run-time-library-behavior.md) Další informace.

## <a name="see-also"></a>Viz také:

- [Nastavení možností linkeru](../../build/reference/linking.md)
