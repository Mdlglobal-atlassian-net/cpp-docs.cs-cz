---
title: Globální stav v CRT
ms.date: 04/02/2020
helpviewer_keywords:
- CRT global state
ms.openlocfilehash: 1b32e8d4f23d2361a52a9b81150ef7c5c7422761
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745365"
---
# <a name="global-state-in-the-crt"></a>Globální stav v CRT

Některé funkce v univerzálním běhu C (UCRT) používají globální stav. Například `setlocale()` nastaví národní prostředí pro celý program, což má vliv na oddělovače číslic, textovou znakovou stránku a tak dále.

Globální stav UCRT není sdílen mezi aplikacemi a os. Například pokud vaše `setlocale()`aplikace volá , nebude mít vliv na národní prostředí pro všechny součásti operačního systému, který používá c run-time nebo naopak.

## <a name="os-specific-versions-of-crt-functions"></a>Verze funkcí CRT specifické pro operační systém

V UCRT mají funkce, které interagují s globálním `_o_`stavem, funkci "dvojče", s předponou . Příklad:

- `setlocale()`ovlivňuje globální stav specifický pro aplikaci.
- `_o_setlocale()`ovlivňuje globální stav sdílený všemi součástmi operačního systému, ale ne aplikacemi.

Jediný rozdíl mezi těmito "twin" funkce je, že při čtení nebo zápisu globální crt stavu, verze `_o_`specifické pro operační systém (to znamená, že verze, které začínají ) použít kopii operačního systému globálního stavu namísto kopie aplikace globálního stavu.

Verze těchto funkcí specifické pro operační `ucrt.osmode.lib`systém jsou v aplikaci . Například verze pro os `setlocale()` specifická pro`_o_setlocale()`

Existují dva způsoby, jak izolovat stav CRT komponenty ze stavu CRT aplikace:

- Staticky propojit komponentu pomocí možnosti kompilátoru /MT (vydání) nebo MTd (ladění). Podrobnosti naleznete v tématu [/MD, /MT, /LD](https://docs.microsoft.com/cpp/build/reference/md-mt-ld-use-run-time-library?view=vs-2019). Všimněte si, že statické propojení může výrazně zvýšit binární velikost.
- Počínaje Windows 10 20H2, získat crt izolace stavu dynamickým propojením crt, ale volání exportu režimu operačního systému (funkce, které začínají _o_). Chcete-li volat exporty režimu operačního systému, staticky propojit jako dříve, ale ignorovat statické UCRT pomocí propojovacího zařízení možnost `/NODEFAULTLIB:libucrt.lib` (vydání) nebo `/NODEFAULTLIB:libucrtd.lib` (ladění) Viz [/NODEFAULTLIB (Ignorovat knihovny)](https://docs.microsoft.com/cpp/build/reference/nodefaultlib-ignore-libraries?view=vs-2019) podrobnosti. A `ucrt.osmode.lib` přidejte do propojovacího nebo linkeru.

> [!Note]
> Ve zdrojovém `setlocale()`kódu `_o_setlocale()`zapište , ne . Při propojení `ucrt.osmode.lib`proti , propojovací systém automaticky nahradí verzi funkce specifické pro operační systém. To znamená, `setlocale()` že bude `_o_setlocale()`nahrazen .

Propojení `ucrt.osmode.lib` proti zakáže některé volání UCRT, které jsou k dispozici pouze v režimu aplikace. Při pokusu o volání těchto bude mít za následek chybu propojení.

## <a name="global-state-affected-by-appos-separation"></a>Globální stav ovlivněný oddělením aplikace/operačního systému

Globální stav ovlivněný oddělením aplikace a stavu operačního systému zahrnuje:

- [Data národního prostředí](locale.md)
- Obslužné rutiny signálu nastavené [signálem](reference/signal.md)
- Rutiny ukončení nastavené [ukončením](reference/set-terminate-crt.md)
- [errno a _doserrno](errno-doserrno-sys-errlist-and-sys-nerr.md)
- Stav generování náhodných čísel používaný [randem](reference/rand.md) a [srandem](reference/srand.md)
- Funkce, které vracejí vyrovnávací paměť, kterou uživatel nemusí uvolnit: [strtok, wcstok, _mbstok](reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) [Tmpnam, _wtmpnam](reference/tempnam-wtempnam-tmpnam-wtmpnam.md) [asctime, _wasctime](reference/asctime-wasctime.md) [gmtime, _gmtime32, _gmtime64](reference/gmtime-gmtime32-gmtime64.md) [_fcvt](reference/fcvt.md) [_ecvt](reference/ecvt.md) [strerror, _strerror, _wcserror, __wcserror](reference/strerror-strerror-wcserror-wcserror.md)
- Vyrovnávací paměť používaná [_putch, _putwch](reference/putch-putwch.md)
- [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)
- [_set_new_handler](reference/set-new-handler.md) a [_set_new_mode](reference/set-new-mode.md)
- To je v pořádku. (text-and-binary-mode-file-i-o.md)
- [Informace o časovém pásmu](time-management.md)

## <a name="see-also"></a>Viz také

[C Odkaz na knihovnu run-time](c-run-time-library-reference.md)
