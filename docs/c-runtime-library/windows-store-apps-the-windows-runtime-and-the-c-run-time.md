---
title: U aplikací pro UPW, prostředí Windows Runtime a C Run-Time
ms.date: 02/02/2019
ms.assetid: 356d6d8d-76ee-4181-9ad0-6f24b2fede38
ms.openlocfilehash: ae57390dc916116b8d799b9f937ff882abaef970
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/06/2019
ms.locfileid: "55763885"
---
# <a name="uwp-apps-the-windows-runtime-and-the-c-run-time"></a>U aplikací pro UPW, prostředí Windows Runtime a C Run-Time

Univerzální aplikace pro platformu Windows (UPW) jsou programy, které běží v modulu Windows Runtime, který se spustí v systému Windows 8. Modul Windows Runtime se odvíjí od důvěryhodného prostředí, které řídí funkce, proměnné a prostředky, které jsou k dispozici pro aplikace pro UPW. Záměrné, zabránit modulu Windows Runtime omezení použití většiny funkcí knihovny Run-Time C (CRT) v aplikacích pro UPW.

Modul Windows Runtime nepodporuje následující funkce CRT:

- Většina funkcí CRT, které se týkají nepodporované funkce.

   Například nelze vytvořit proces pomocí aplikace pro UPW **exec** a **vytvořit podřízený proces** rodiny rutin.

   Když se v aplikaci UWP, že je skutečnost uvedena v článku o jeho nepodporuje funkce CRT.

- Většina vícebajtové znakové a řetězcové funkce.

   Text kódování Unicode a ANSI jsou však podporovány.

- Proměnné prostředí.

- Koncept aktuálního pracovního adresáře.

- UPW aplikace a knihovny DLL, které jsou staticky propojeny CRT a vytvořené s použitím [/MT](../build/reference/md-mt-ld-use-run-time-library.md) nebo `/MTd` – možnosti kompilátoru.

   To znamená, aplikaci, která se použije vícevláknovou statickou verzi CRT.

- Aplikace, která je vytvořená pomocí [/MDd](../build/reference/md-mt-ld-use-run-time-library.md) – možnost kompilátoru.

   To znamená, ladění, Vícevláknová a knihovnu DLL verzi CRT. V modulu Windows Runtime nepodporuje takové aplikace.

Úplný seznam funkcí CRT, které nejsou k dispozici v aplikaci UPW a návrhů týkajících se alternativní funkcí najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="see-also"></a>Viz také

[Kompatibilita](../c-runtime-library/compatibility.md)<br/>
[Nepodporované funkce CRT prostředí Windows Runtime](../c-runtime-library/windows-runtime-unsupported-crt-functions.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Vytvoření konzolové aplikace univerzální platformy Windows](/windows/uwp/launch-resume/console-uwp)
